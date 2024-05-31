# Parameter Management
Once we have chosen an architecture
and set our hyperparameters,
we proceed to the training loop,
where our goal is to find parameter values
that minimize our loss function.
After training, we will need these parameters
in order to make future predictions.
Additionally, we will sometimes wish
to extract the parameters
either to reuse them in some other context,
to save our model to disk so that
it may be executed in other software,
or for examination in the hope of
gaining scientific understanding.
Most of the time, we will be able
to ignore the nitty-gritty details
of how parameters are declared
and manipulated, relying on deep learning frameworks
to do the heavy lifting.
However, when we move away from
stacked architectures with standard layers,
we will sometimes need to get into the weeds
of declaring and manipulating parameters.
In this section, we cover the following:
* Accessing parameters for debugging, diagnostics, and visualizations.
* Parameter initialization.
* Sharing parameters across different model components.
We start by focusing on an MLP with one hidden layer.
```{.python .input}
#@tab pytorch
import torch
from torch import nn
net = nn.Sequential(nn.Linear(4, 8), nn.ReLU(), nn.Linear(8, 1))
X = torch.rand(size=(2, 4))
net(X)
```
## Parameter Access
Let us start with how to access parameters
from the models that you already know.
When a model is defined via the `Sequential` class,
we can first access any layer by indexing
into the model as though it were a list.
Each layer's parameters are conveniently
located in its attribute.
We can inspect the parameters of the second fully-connected layer as follows.
```{.python .input}
#@tab pytorch
print(net[2].state_dict())
```
The output tells us a few important things.
First, this fully-connected layer
contains two parameters,
corresponding to that layer's
weights and biases, respectively.
Both are stored as single precision floats (float32).
Note that the names of the parameters
allow us to uniquely identify
each layer's parameters,
even in a network containing hundreds of layers.
### Targeted Parameters
Note that each parameter is represented
as an instance of the parameter class.
To do anything useful with the parameters,
we first need to access the underlying numerical values.
There are several ways to do this.
Some are simpler while others are more general.
The following code extracts the bias
from the second fully-connected layer (i.e. the third neural network layer), 
which returns a parameter class instance, and 
further accesses that parameter's value.
```{.python .input}
#@tab pytorch
print(type(net[2].bias))
print(net[2].bias)
print(net[2].bias.data)
```
:begin_tab:`mxnet,pytorch`
Parameters are complex objects,
containing values, gradients,
and additional information.
That's why we need to request the value explicitly.
In addition to the value, each parameter also allows us to access the gradient. Because we have not invoked backpropagation for this network yet, it is in its initial state.
:end_tab:
```{.python .input}
#@tab pytorch
net[2].weight.grad == None
```
### All Parameters at Once
When we need to perform operations on all parameters,
accessing them one-by-one can grow tedious.
The situation can grow especially unwieldy
when we work with more complex blocks (e.g., nested blocks),
since we would need to recurse
through the entire tree to extract
each sub-block's parameters. Below we demonstrate accessing the parameters of the first fully-connected layer vs. accessing all layers.
```{.python .input}
#@tab pytorch
print(*[(name, param.shape) for name, param in net[0].named_parameters()])
print(*[(name, param.shape) for name, param in net.named_parameters()])
```
This provides us with another way of accessing the parameters of the network as follows.
```{.python .input}
#@tab pytorch
net.state_dict()['2.bias'].data
```
### Collecting Parameters from Nested Blocks
Let us see how the parameter naming conventions work
if we nest multiple blocks inside each other.
For that we first define a function that produces blocks
(a block factory, so to speak) and then
combine these inside yet larger blocks.
```{.python .input}
#@tab pytorch
def block1():
    return nn.Sequential(nn.Linear(4, 8), nn.ReLU(),
                         nn.Linear(8, 4), nn.ReLU())
def block2():
    net = nn.Sequential()
    for i in range(4):
        # Nested here
        net.add_module(f'block {i}', block1())
    return net
rgnet = nn.Sequential(block2(), nn.Linear(4, 1))
rgnet(X)
```
Now that we have designed the network,
let us see how it is organized.
```{.python .input}
#@tab pytorch
print(rgnet)
```
Since the layers are hierarchically nested,
we can also access them as though
indexing through nested lists.
For instance, we can access the first major block,
within it the second sub-block,
and within that the bias of the first layer,
with as follows.
```{.python .input}
#@tab pytorch
rgnet[0][1][0].bias.data
```
## Parameter Initialization
Now that we know how to access the parameters,
let us look at how to initialize them properly.
We discussed the need for proper initialization in :numref:`sec_numerical_stability`.
The deep learning framework provides default random initializations to its layers.
However, we often want to initialize our weights
according to various other protocols. The framework provides most commonly
used protocols, and also allows to create a custom initializer.
:begin_tab:`mxnet`
By default, MXNet initializes weight parameters by randomly drawing from a uniform distribution $U(-0.07, 0.07)$,
clearing bias parameters to zero.
MXNet's `init` module provides a variety
of preset initialization methods.
:end_tab:
:begin_tab:`pytorch`
By default, PyTorch initializes weight and bias matrices
uniformly by drawing from a range that is computed according to the input and output dimension.
PyTorch's `nn.init` module provides a variety
of preset initialization methods.
:end_tab:
:begin_tab:`tensorflow`
By default, Keras initializes weight matrices uniformly by drawing from a range that is computed according to the input and output dimension, and the bias parameters are all set to zero.
TensorFlow provides a variety of initialization methods both in the root module and the `keras.initializers` module.
:end_tab:
### Built-in Initialization
Let us begin by calling on built-in initializers.
The code below initializes all weight parameters
as Gaussian random variables
with standard deviation 0.01, while bias parameters cleared to zero.
```{.python .input}
#@tab pytorch
def init_normal(m):
    if type(m) == nn.Linear:
        nn.init.normal_(m.weight, mean=0, std=0.01)
        nn.init.zeros_(m.bias)
net.apply(init_normal)
net[0].weight.data[0], net[0].bias.data[0]
```
We can also initialize all the parameters
to a given constant value (say, 1).
```{.python .input}
#@tab pytorch
def init_constant(m):
    if type(m) == nn.Linear:
        nn.init.constant_(m.weight, 1)
        nn.init.zeros_(m.bias)
net.apply(init_constant)
net[0].weight.data[0], net[0].bias.data[0]
```
We can also apply different initializers for certain blocks.
For example, below we initialize the first neural network layer
with the Xavier initializer
and initialize the third neural network layer
to a constant value of 42.
```{.python .input}
#@tab pytorch
def xavier(m):
    if type(m) == nn.Linear:
        torch.nn.init.xavier_uniform_(m.weight)
def init_42(m):
    if type(m) == nn.Linear:
        torch.nn.init.constant_(m.weight, 42)
net[0].apply(xavier)
net[2].apply(init_42)
print(net[0].weight.data[0])
print(net[2].weight.data)
```
### Custom Initialization
Sometimes, the initialization methods we need
are not provided by the deep learning framework.
In the example below, we define an initializer
for any weight parameter $w$ using the following strange distribution:
$$
\begin{aligned}
    w \sim \begin{cases}
        U(5, 10) & \text{ with probability } \frac{1}{4} \\
            0    & \text{ with probability } \frac{1}{2} \\
        U(-10, -5) & \text{ with probability } \frac{1}{4}
    \end{cases}
\end{aligned}
$$
:begin_tab:`mxnet`
Here we define a subclass of the `Initializer` class.
Usually, we only need to implement the `_init_weight` function
which takes a tensor argument (`data`)
and assigns to it the desired initialized values.
:end_tab:
:begin_tab:`pytorch`
Again, we implement a `my_init` function to apply to `net`.
:end_tab:
:begin_tab:`tensorflow`
Here we define a subclass of `Initializer` and implement the `__call__`
function that return a desired tensor given the shape and data type.
:end_tab:
```{.python .input}
#@tab pytorch
def my_init(m):
    if type(m) == nn.Linear:
        print("Init", *[(name, param.shape) 
                        for name, param in m.named_parameters()][0])
        nn.init.uniform_(m.weight, -10, 10)
        m.weight.data *= m.weight.data.abs() >= 5
net.apply(my_init)
net[0].weight[:2]
```
Note that we always have the option
of setting parameters directly.
```{.python .input}
#@tab pytorch
net[0].weight.data[:] += 1
net[0].weight.data[0, 0] = 42
net[0].weight.data[0]
```
:begin_tab:`mxnet`
A note for advanced users:
if you want to adjust parameters within an `autograd` scope,
you need to use `set_data` to avoid confusing
the automatic differentiation mechanics.
:end_tab:
## Tied Parameters
Often, we want to share parameters across multiple layers.
Let us see how to do this elegantly.
In the following we allocate a dense layer
and then use its parameters specifically
to set those of another layer.
```{.python .input}
#@tab pytorch
# We need to give the shared layer a name so that we can refer to its
# parameters
shared = nn.Linear(8, 8)
net = nn.Sequential(nn.Linear(4, 8), nn.ReLU(),
                    shared, nn.ReLU(),
                    shared, nn.ReLU(),
                    nn.Linear(8, 1))
net(X)
# Check whether the parameters are the same
print(net[2].weight.data[0] == net[4].weight.data[0])
net[2].weight.data[0, 0] = 100
# Make sure that they are actually the same object rather than just having the
# same value
print(net[2].weight.data[0] == net[4].weight.data[0])
```
:begin_tab:`mxnet`
This example shows that the parameters
of the second and third layer are tied.
They are not just equal, they are
represented by the same exact tensor.
Thus, if we change one of the parameters,
the other one changes, too.
You might wonder,
when parameters are tied
what happens to the gradients?
Since the model parameters contain gradients,
the gradients of the second hidden layer
and the third hidden layer are added together
during backpropagation.
:end_tab:
:begin_tab:`pytorch`
This example shows that the parameters
of the third and fifth neural network layer are tied.
They are not just equal, they are
represented by the same exact tensor.
Thus, if we change one of the parameters,
the other one changes, too.
You might wonder,
when parameters are tied
what happens to the gradients?
Since the model parameters contain gradients,
the gradients of the second hidden layer (i.e. the third neural network layer)
and the third hidden layer (i.e. the fifth neural network layer) are added together
during backpropagation.
:end_tab:
## Summary
* We have several ways to access, initialize, and tie model parameters.
* We can use custom initialization.
## Exercises
1. Use the `FancyMLP` model defined in :numref:`sec_model_construction` and access the parameters of the various layers.
1. Look at the initialization module document to explore different initializers.
1. Construct an MLP containing a shared parameter layer and train it. During the training process, observe the model parameters and gradients of each layer.
1. Why is sharing parameters a good idea?
:begin_tab:`mxnet`
[Discussions](https://discuss.d2l.ai/t/56)
:end_tab:
:begin_tab:`pytorch`
[Discussions](https://discuss.d2l.ai/t/57)
:end_tab:
:begin_tab:`tensorflow`
[Discussions](https://discuss.d2l.ai/t/269)
:end_tab: