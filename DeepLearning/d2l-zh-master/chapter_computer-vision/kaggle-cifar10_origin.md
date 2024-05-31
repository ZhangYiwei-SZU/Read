# Image Classification (CIFAR-10) on Kaggle
:label:`sec_kaggle_cifar10`
So far, we have been using high-level APIs of deep learning frameworks to directly obtain image datasets in tensor format. 
However, custom image datasets 
often come in the form of image files.
In this section, we will start from 
raw image files, 
and organize, read, then transform them
into tensor format step by step.
We experimented with the CIFAR-10 dataset in :numref:`sec_image_augmentation`,
which is an important dataset in computer vision.
In this section,
we will apply the knowledge we learned 
in previous sections
to practice the Kaggle competition of
CIFAR-10 image classification. 
The web address of the competition is https://www.kaggle.com/c/cifar-10
:numref:`fig_kaggle_cifar10` shows the information on the competition's webpage.
In order to submit the results, 
you need to register a Kaggle account.
![CIFAR-10 image classification competition webpage information. The competition dataset can be obtained by clicking the "Data" tab.](../img/kaggle-cifar10.png)
:width:`600px`
:label:`fig_kaggle_cifar10`
```{.python .input}
#@tab pytorch
import collections
from d2l import torch as d2l
import math
import torch
import torchvision
from torch import nn
import os
import pandas as pd
import shutil
```
## Obtaining and Organizing the Dataset
The competition dataset is divided into 
a training set and a test set,
which contain 50000 and 300000 images, respectively.
In the test set,
10000 images will be used for evaluation, 
while the remaining 290000 images will not 
be evaluated: 
they are included just
to make it hard
to cheat with
*manually* labeled results of the test set.
The images in this dataset
are all png color (RGB channels) image files,
whose height and width are both 32 pixels.
The images cover a total of 10 categories, namely airplanes, cars, birds, cats, deer, dogs, frogs, horses, boats, and trucks.
The upper left corner of :numref:`fig_kaggle_cifar10` shows some images of airplanes, cars, and birds in the dataset.
### Downloading the Dataset
After logging in to Kaggle, we can click the "Data" tab on the CIFAR-10 image classification competition webpage shown in :numref:`fig_kaggle_cifar10` and download the dataset by clicking the "Download All" button.
After unzipping the downloaded file in `../data`, and unzipping `train.7z` and `test.7z` inside it, you will find the entire dataset in the following paths:
* `../data/cifar-10/train/[1-50000].png`
* `../data/cifar-10/test/[1-300000].png`
* `../data/cifar-10/trainLabels.csv`
* `../data/cifar-10/sampleSubmission.csv`
where the `train` and `test` directories contain the training and testing images, respectively, `trainLabels.csv` provides labels for the training images, and `sample_submission.csv` is a sample submission file.
To make it easier to get started, we provide a small-scale sample of the dataset that
contains the first 1000 training images and 5 random testing images.
To use the full dataset of the Kaggle competition, you need to set the following `demo` variable to `False`.
### Organizing the Dataset
We need to organize datasets to facilitate model training and testing. 
Let us first read the labels from the csv file.
The following function returns a dictionary that maps
the non-extension part of the filename to its label.
Next, we define the `reorg_train_valid` function to split the validation set out of the original training set.
The argument `valid_ratio` in this function is the ratio of the number of examples in the validation set to the number of examples in the original training set.
More concretely,
let $n$ be the number of images of the class with the least examples, and $r$ be the ratio. 
The validation set will split out
$\max(\lfloor nr\rfloor,1)$ images for each class.
Let us use `valid_ratio=0.1` as an example. Since the original training set has 50000 images,
there will be 45000 images used for training in the path `train_valid_test/train`,
while the other 5000 images will be split out
as validation set in the path `train_valid_test/valid`. After organizing the dataset, images of the same class will be placed under the same folder.
The `reorg_test` function below organizes the testing set for data loading during prediction.
Finally, we use a function to invoke
the `read_csv_labels`, `reorg_train_valid`, and `reorg_test` functions defined above.
Here we only set the batch size to 4 for the small-scale sample of the dataset.
When training and testing
the complete dataset of the Kaggle competition,
`batch_size` should be set to a larger integer, such as 128.
We split out 10% of the training examples as the validation set for tuning hyperparameters.
## Image Augmentation
We use image augmentation to address overfitting.
For example, images can be flipped horizontally at random during training.
We can also perform standardization for the three RGB channels of color images. Below lists some of these operations that you can tweak.
```{.python .input}
#@tab pytorch
transform_train = torchvision.transforms.Compose([
    # Scale the image up to a square of 40 pixels in both height and width
    torchvision.transforms.Resize(40),
    # Randomly crop a square image of 40 pixels in both height and width to
    # produce a small square of 0.64 to 1 times the area of the original
    # image, and then scale it to a square of 32 pixels in both height and
    # width
    torchvision.transforms.RandomResizedCrop(32, scale=(0.64, 1.0),
                                                   ratio=(1.0, 1.0)),
    torchvision.transforms.RandomHorizontalFlip(),
    torchvision.transforms.ToTensor(),
    # Standardize each channel of the image
    torchvision.transforms.Normalize([0.4914, 0.4822, 0.4465],
                                     [0.2023, 0.1994, 0.2010])])
```
During testing,
we only perform standardization on images
so as to
remove randomness in the evaluation results.
```{.python .input}
#@tab pytorch
transform_test = torchvision.transforms.Compose([
    torchvision.transforms.ToTensor(),
    torchvision.transforms.Normalize([0.4914, 0.4822, 0.4465],
                                     [0.2023, 0.1994, 0.2010])])
```
## Reading the Dataset
Next, we read the organized dataset consisting of raw image files. Each example includes an image and a label.
```{.python .input}
#@tab pytorch
train_ds, train_valid_ds = [torchvision.datasets.ImageFolder(
    os.path.join(data_dir, 'train_valid_test', folder),
    transform=transform_train) for folder in ['train', 'train_valid']]
valid_ds, test_ds = [torchvision.datasets.ImageFolder(
    os.path.join(data_dir, 'train_valid_test', folder),
    transform=transform_test) for folder in ['valid', 'test']]
```
During training,
we need to specify all the image augmentation operations defined above.
When the validation set
is used for model evaluation during hyperparameter tuning,
no randomness from image augmentation should be introduced.
Before final prediction,
we train the model on the combined training set and validation set to make full use of all the labeled data.
```{.python .input}
#@tab pytorch
train_iter, train_valid_iter = [torch.utils.data.DataLoader(
    dataset, batch_size, shuffle=True, drop_last=True)
    for dataset in (train_ds, train_valid_ds)]
valid_iter = torch.utils.data.DataLoader(valid_ds, batch_size, shuffle=False,
                                         drop_last=True)
test_iter = torch.utils.data.DataLoader(test_ds, batch_size, shuffle=False,
                                        drop_last=False)
```
## Defining the Model
:begin_tab:`mxnet`
Here, we build the residual blocks based on the `HybridBlock` class, which is
slightly different from the implementation described in
:numref:`sec_resnet`.
This is for improving computational efficiency.
:end_tab:
:begin_tab:`mxnet`
Next, we define the ResNet-18 model.
:end_tab:
:begin_tab:`mxnet`
We use Xavier initialization described in :numref:`subsec_xavier` before training begins.
:end_tab:
:begin_tab:`pytorch`
We define the ResNet-18 model described in
:numref:`sec_resnet`.
:end_tab:
```{.python .input}
#@tab pytorch
def get_net():
    num_classes = 10
    net = d2l.resnet18(num_classes, 3)
    return net
loss = nn.CrossEntropyLoss(reduction="none")
```
## Defining the Training Function
We will select models and tune hyperparameters according to the model's performance on the validation set. 
In the following, we define the model training function `train`.
```{.python .input}
#@tab pytorch
def train(net, train_iter, valid_iter, num_epochs, lr, wd, devices, lr_period,
          lr_decay):
    trainer = torch.optim.SGD(net.parameters(), lr=lr, momentum=0.9,
                              weight_decay=wd)
    scheduler = torch.optim.lr_scheduler.StepLR(trainer, lr_period, lr_decay)
    num_batches, timer = len(train_iter), d2l.Timer()
    animator = d2l.Animator(xlabel='epoch', xlim=[1, num_epochs],
                            legend=['train loss', 'train acc', 'valid acc'])
    net = nn.DataParallel(net, device_ids=devices).to(devices[0])
    for epoch in range(num_epochs):
        net.train()
        metric = d2l.Accumulator(3)
        for i, (features, labels) in enumerate(train_iter):
            timer.start()
            l, acc = d2l.train_batch_ch13(net, features, labels,
                                          loss, trainer, devices)
            metric.add(l, acc, labels.shape[0])
            timer.stop()
            if (i + 1) % (num_batches // 5) == 0 or i == num_batches - 1:
                animator.add(epoch + (i + 1) / num_batches,
                             (metric[0] / metric[2], metric[1] / metric[2],
                              None))
        if valid_iter is not None:
            valid_acc = d2l.evaluate_accuracy_gpu(net, valid_iter)
            animator.add(epoch + 1, (None, None, valid_acc))
        scheduler.step()
    if valid_iter is not None:
        print(f'loss {metric[0] / metric[2]:.3f}, '
              f'train acc {metric[1] / metric[2]:.3f}, '
              f'valid acc {valid_acc:.3f}')
    else:
        print(f'loss {metric[0] / metric[2]:.3f}, '
              f'train acc {metric[1] / metric[2]:.3f}')
    print(f'{metric[2] * num_epochs / timer.sum():.1f} examples/sec '
          f'on {str(devices)}')
```
## Training and Validating the Model
Now, we can train and validate the model.
All the following hyperparameters can be tuned.
For example, we can increase the number of epochs.
When `lr_period` and `lr_decay` are set to 50 and 0.1, respectively, the learning rate of the optimization algorithm will be multiplied by 0.1 after every 50 epochs. Just for demonstration,
we only train 5 epochs here.
```{.python .input}
#@tab pytorch
devices, num_epochs, lr, wd = d2l.try_all_gpus(), 5, 0.1, 5e-4
lr_period, lr_decay, net = 50, 0.1, get_net()
train(net, train_iter, valid_iter, num_epochs, lr, wd, devices, lr_period,
      lr_decay)
```
## Classifying the Testing Set and Submitting Results on Kaggle
After obtaining a promising model with hyperparameters,
we use all the labeled data (including the validation set) to retrain the model and classify the testing set.
```{.python .input}
#@tab pytorch
net, preds = get_net(), []
train(net, train_valid_iter, None, num_epochs, lr, wd, devices, lr_period,
      lr_decay)
for X, _ in test_iter:
    y_hat = net(X.to(devices[0]))
    preds.extend(y_hat.argmax(dim=1).type(torch.int32).cpu().numpy())
sorted_ids = list(range(1, len(test_ds) + 1))
sorted_ids.sort(key=lambda x: str(x))
df = pd.DataFrame({'id': sorted_ids, 'label': preds})
df['label'] = df['label'].apply(lambda x: train_valid_ds.classes[x])
df.to_csv('submission.csv', index=False)
```
The above code
will generate a `submission.csv` file,
whose format
meets the requirement of the Kaggle competition.
The method
for submitting results to Kaggle
is similar to that in :numref:`sec_kaggle_house`.
## Summary
* We can read datasets containing raw image files after organizing them into the required format.
:begin_tab:`mxnet`
* We can use convolutional neural networks, image augmentation, and hybrid programing in an image classification competition.
:end_tab:
:begin_tab:`pytorch`
* We can use convolutional neural networks and image augmentation in an image classification competition.
:end_tab:
## Exercises
1. Use the complete CIFAR-10 dataset for this Kaggle competition. Change the `batch_size` and number of epochs `num_epochs` to 128 and 100, respectively.  See what accuracy and ranking you can achieve in this competition. Can you further improve them?
1. What accuracy can you get when not using image augmentation?
:begin_tab:`mxnet`
[Discussions](https://discuss.d2l.ai/t/379)
:end_tab:
:begin_tab:`pytorch`
[Discussions](https://discuss.d2l.ai/t/1479)
:end_tab: