# Predicting House Prices on Kaggle
:label:`sec_kaggle_house`
Now that we have introduced some basic tools
for building and training deep networks
and regularizing them with techniques including
weight decay and dropout,
we are ready to put all this knowledge into practice
by participating in a Kaggle competition.
The house price prediction competition
is a great place to start.
The data are fairly generic and do not exhibit exotic structure
that might require specialized models (as audio or video might).
This dataset, collected by Bart de Cock in 2011 :cite:`De-Cock.2011`,
covers house prices in Ames, IA from the period of 2006--2010.
It is considerably larger than the famous [Boston housing dataset](https://archive.ics.uci.edu/ml/machine-learning-databases/housing/housing.names) of Harrison and Rubinfeld (1978),
boasting both more examples and more features.
In this section, we will walk you through details of
data preprocessing, model design, and hyperparameter selection.
We hope that through a hands-on approach,
you will gain some intuitions that will guide you
in your career as a data scientist.
## Downloading and Caching Datasets
Throughout the book, we will train and test models
on various downloaded datasets.
Here, we implement several utility functions
to facilitate data downloading.
First, we maintain a dictionary `DATA_HUB`
that maps a string (the *name* of the dataset)
to a tuple containing both the URL to locate the dataset
and the SHA-1 key that verifies the integrity of the file.
All such datasets are hosted at the site
whose address is `DATA_URL`.
The following `download` function downloads a dataset,
caching it in a local directory (`../data` by default)
and returns the name of the downloaded file.
If a file corresponding to this dataset
already exists in the cache directory
and its SHA-1 matches the one stored in `DATA_HUB`,
our code will use the cached file to avoid
clogging up your internet with redundant downloads.
We also implement two additional utility functions:
one is to download and extract a zip or tar file
and the other to download all the datasets used in this book from `DATA_HUB` into the cache directory.
## Kaggle
[Kaggle](https://www.kaggle.com) is a popular platform
that hosts machine learning competitions.
Each competition centers on a dataset and many
are sponsored by stakeholders who offer prizes
to the winning solutions.
The platform helps users to interact
via forums and shared code,
fostering both collaboration and competition.
While leaderboard chasing often spirals out of control,
with researchers focusing myopically on preprocessing steps
rather than asking fundamental questions,
there is also tremendous value in the objectivity of a platform
that facilitates direct quantitative comparisons
among competing approaches as well as code sharing
so that everyone can learn what did and did not work.
If you want to participate in a Kaggle competitions,
you will first need to register for an account
(see :numref:`fig_kaggle`).
![The Kaggle website.](../img/kaggle.png)
:width:`400px`
:label:`fig_kaggle`
On the house price prediction competition page, as illustrated
in :numref:`fig_house_pricing`,
you can find the dataset (under the "Data" tab),
submit predictions, and see your ranking,
The URL is right here:
> https://www.kaggle.com/c/house-prices-advanced-regression-techniques
![The house price prediction competition page.](../img/house-pricing.png)
:width:`400px`
:label:`fig_house_pricing`
## Accessing and Reading the Dataset
Note that the competition data is separated
into training and test sets.
Each record includes the property value of the house
and attributes such as street type, year of construction,
roof type, basement condition, etc.
The features consist of various data types.
For example, the year of construction
is represented by an integer,
the roof type by discrete categorical assignments,
and other features by floating point numbers.
And here is where reality complicates things:
for some examples, some data are altogether missing
with the missing value marked simply as "na".
The price of each house is included
for the training set only
(it is a competition after all).
We will want to partition the training set
to create a validation set,
but we only get to evaluate our models on the official test set
after uploading predictions to Kaggle.
The "Data" tab on the competition tab
in :numref:`fig_house_pricing`
has links to download the data.
To get started, we will read in and process the data
using `pandas`, which we have introduced in :numref:`sec_pandas`.
So, you will want to make sure that you have `pandas` installed
before proceeding further.
Fortunately, if you are reading in Jupyter,
we can install pandas without even leaving the notebook.
```{.python .input}
#@tab pytorch
# If pandas is not installed, please uncomment the following line:
# !pip install pandas
%matplotlib inline
from d2l import torch as d2l
import torch
import torch.nn as nn
import pandas as pd
import numpy as np
```
For convenience, we can download and cache
the Kaggle housing dataset
using the script we defined above.
We use `pandas` to load the two csv files containing training and test data respectively.
The training dataset includes 1460 examples,
80 features, and 1 label, while the test data
contains 1459 examples and 80 features.
Let us take a look at the first four and last two features
as well as the label (SalePrice) from the first four examples.
We can see that in each example, the first feature is the ID.
This helps the model identify each training example.
While this is convenient, it does not carry
any information for prediction purposes.
Hence, we remove it from the dataset
before feeding the data into the model.
## Data Preprocessing
As stated above, we have a wide variety of data types.
We will need to preprocess the data before we can start modeling.
Let us start with the numerical features.
First, we apply a heuristic,
replacing all missing values
by the corresponding feature's mean.
Then, to put all features on a common scale,
we *standardize* the data by
rescaling features to zero mean and unit variance:
$$x \leftarrow \frac{x - \mu}{\sigma}.$$
To verify that this indeed transforms
our feature (variable) such that it has zero mean and unit variance,
note that $E[\frac{x-\mu}{\sigma}] = \frac{\mu - \mu}{\sigma} = 0$
and that $E[(x-\mu)^2] = (\sigma^2 + \mu^2) - 2\mu^2+\mu^2 = \sigma^2$.
Intuitively, we standardize the data
for two reasons.
First, it proves convenient for optimization.
Second, because we do not know *a priori*
which features will be relevant,
we do not want to penalize coefficients
assigned to one feature more than on any other.
Next we deal with discrete values.
This includes features such as "MSZoning".
We replace them by a one-hot encoding
in the same way that we previously transformed
multiclass labels into vectors (see :numref:`subsec_classification-problem`).
For instance, "MSZoning" assumes the values "RL" and "RM".
Dropping the "MSZoning" feature,
two new indicator features
"MSZoning_RL" and "MSZoning_RM" are created with values being either 0 or 1.
According to one-hot encoding,
if the original value of "MSZoning" is "RL",
then "MSZoning_RL" is 1 and "MSZoning_RM" is 0.
The `pandas` package does this automatically for us.
You can see that this conversion increases
the number of features from 79 to 331.
Finally, via the `values` attribute,
we can extract the NumPy format from the `pandas` format
and convert it into the tensor
representation for training.
## Training
To get started we train a linear model with squared loss.
Not surprisingly, our linear model will not lead
to a competition-winning submission
but it provides a sanity check to see whether
there is meaningful information in the data.
If we cannot do better than random guessing here,
then there might be a good chance
that we have a data processing bug.
And if things work, the linear model will serve as a baseline
giving us some intuition about how close the simple model
gets to the best reported models, giving us a sense
of how much gain we should expect from fancier models.
```{.python .input}
#@tab pytorch
loss = nn.MSELoss()
in_features = train_features.shape[1]
def get_net():
    net = nn.Sequential(nn.Linear(in_features,1))
    return net
```
With house prices, as with stock prices,
we care about relative quantities
more than absolute quantities.
Thus we tend to care more about
the relative error $\frac{y - \hat{y}}{y}$
than about the absolute error $y - \hat{y}$.
For instance, if our prediction is off by USD 100,000
when estimating the price of a house in Rural Ohio,
where the value of a typical house is 125,000 USD,
then we are probably doing a horrible job.
On the other hand, if we err by this amount
in Los Altos Hills, California,
this might represent a stunningly accurate prediction
(there, the median house price exceeds 4 million USD).
One way to address this problem is to
measure the discrepancy in the logarithm of the price estimates.
In fact, this is also the official error measure
used by the competition to evaluate the quality of submissions.
After all, a small value $\delta$ for $|\log y - \log \hat{y}| \leq \delta$
translates into $e^{-\delta} \leq \frac{\hat{y}}{y} \leq e^\delta$.
This leads to the following root-mean-squared-error between the logarithm of the predicted price and the logarithm of the label price:
$$\sqrt{\frac{1}{n}\sum_{i=1}^n\left(\log y_i -\log \hat{y}_i\right)^2}.$$
```{.python .input}
#@tab pytorch
def log_rmse(net, features, labels):
    # To further stabilize the value when the logarithm is taken, set the
    # value less than 1 as 1
    clipped_preds = torch.clamp(net(features), 1, float('inf'))
    rmse = torch.sqrt(torch.mean(loss(torch.log(clipped_preds),
                                       torch.log(labels))))
    return rmse.item()
```
Unlike in previous sections, our training functions
will rely on the Adam optimizer
(we will describe it in greater detail later).
The main appeal of this optimizer is that,
despite doing no better (and sometimes worse)
given unlimited resources for hyperparameter optimization,
people tend to find that it is significantly less sensitive
to the initial learning rate.
```{.python .input}
#@tab pytorch
def train(net, train_features, train_labels, test_features, test_labels,
          num_epochs, learning_rate, weight_decay, batch_size):
    train_ls, test_ls = [], []
    train_iter = d2l.load_array((train_features, train_labels), batch_size)
    # The Adam optimization algorithm is used here
    optimizer = torch.optim.Adam(net.parameters(),
                                 lr = learning_rate,
                                 weight_decay = weight_decay)
    for epoch in range(num_epochs):
        for X, y in train_iter:
            optimizer.zero_grad()
            l = loss(net(X), y)
            l.backward()
            optimizer.step()
        train_ls.append(log_rmse(net, train_features, train_labels))
        if test_labels is not None:
            test_ls.append(log_rmse(net, test_features, test_labels))
    return train_ls, test_ls
```
## $K$-Fold Cross-Validation
You might recall that we introduced $K$-fold cross-validation
in the section where we discussed how to deal
with model selection (:numref:`sec_model_selection`).
We will put this to good use to select the model design
and to adjust the hyperparameters.
We first need a function that returns
the $i^\mathrm{th}$ fold of the data
in a $K$-fold cross-validation procedure.
It proceeds by slicing out the $i^\mathrm{th}$ segment
as validation data and returning the rest as training data.
Note that this is not the most efficient way of handling data
and we would definitely do something much smarter
if our dataset was considerably larger.
But this added complexity might obfuscate our code unnecessarily
so we can safely omit it here owing to the simplicity of our problem.
The training and verification error averages are returned
when we train $K$ times in the $K$-fold cross-validation.
## Model Selection
In this example, we pick an untuned set of hyperparameters
and leave it up to the reader to improve the model.
Finding a good choice can take time,
depending on how many variables one optimizes over.
With a large enough dataset,
and the normal sorts of hyperparameters,
$K$-fold cross-validation tends to be
reasonably resilient against multiple testing.
However, if we try an unreasonably large number of options
we might just get lucky and find that our validation
performance is no longer representative of the true error.
Notice that sometimes the number of training errors
for a set of hyperparameters can be very low,
even as the number of errors on $K$-fold cross-validation
is considerably higher.
This indicates that we are overfitting.
Throughout training you will want to monitor both numbers.
Less overfitting might indicate that our data can support a more powerful model.
Massive overfitting might suggest that we can gain
by incorporating regularization techniques.
##  Submitting Predictions on Kaggle
Now that we know what a good choice of hyperparameters should be,
we might as well use all the data to train on it
(rather than just $1-1/K$ of the data
that are used in the cross-validation slices).
The model that we obtain in this way
can then be applied to the test set.
Saving the predictions in a csv file
will simplify uploading the results to Kaggle.
One nice sanity check is to see
whether the predictions on the test set
resemble those of the $K$-fold cross-validation process.
If they do, it is time to upload them to Kaggle.
The following code will generate a file called `submission.csv`.
Next, as demonstrated in :numref:`fig_kaggle_submit2`,
we can submit our predictions on Kaggle
and see how they compare with the actual house prices (labels)
on the test set.
The steps are quite simple:
* Log in to the Kaggle website and visit the house price prediction competition page.
* Click the “Submit Predictions” or “Late Submission” button (as of this writing, the button is located on the right).
* Click the “Upload Submission File” button in the dashed box at the bottom of the page and select the prediction file you wish to upload.
* Click the “Make Submission” button at the bottom of the page to view your results.
![Submitting data to Kaggle](../img/kaggle-submit2.png)
:width:`400px`
:label:`fig_kaggle_submit2`
## Summary
* Real data often contain a mix of different data types and need to be preprocessed.
* Rescaling real-valued data to zero mean and unit variance is a good default. So is replacing missing values with their mean.
* Transforming categorical features into indicator features allows us to treat them like one-hot vectors.
* We can use $K$-fold cross-validation to select the model and adjust the hyperparameters.
* Logarithms are useful for relative errors.
## Exercises
1. Submit your predictions for this section to Kaggle. How good are your predictions?
1. Can you improve your model by minimizing the logarithm of prices directly? What happens if you try to predict the logarithm of the price rather than the price?
1. Is it always a good idea to replace missing values by their mean? Hint: can you construct a situation where the values are not missing at random?
1. Improve the score on Kaggle by tuning the hyperparameters through $K$-fold cross-validation.
1. Improve the score by improving the model (e.g., layers, weight decay, and dropout).
1. What happens if we do not standardize the continuous numerical features like what we have done in this section?
:begin_tab:`mxnet`
[Discussions](https://discuss.d2l.ai/t/106)
:end_tab:
:begin_tab:`pytorch`
[Discussions](https://discuss.d2l.ai/t/107)
:end_tab:
:begin_tab:`tensorflow`
[Discussions](https://discuss.d2l.ai/t/237)
:end_tab: