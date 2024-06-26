# File I/O
So far we discussed how to process data and how
to build, train, and test deep learning models.
However, at some point, we will hopefully be happy enough
with the learned models that we will want
to save the results for later use in various contexts
(perhaps even to make predictions in deployment).
Additionally, when running a long training process,
the best practice is to periodically save intermediate results (checkpointing)
to ensure that we do not lose several days worth of computation
if we trip over the power cord of our server.
Thus it is time to learn how to load and store
both individual weight vectors and entire models.
This section addresses both issues.
## Loading and Saving Tensors
For individual tensors, we can directly
invoke the `load` and `save` functions
to read and write them respectively.
Both functions require that we supply a name,
and `save` requires as input the variable to be saved.
```{.python .input}
#@tab pytorch
import torch
from torch import nn
from torch.nn import functional as F
x = torch.arange(4)
torch.save(x, 'x-file')
```
We can now read the data from the stored file back into memory.
```{.python .input}
#@tab pytorch
x2 = torch.load("x-file")
x2
```
We can store a list of tensors and read them back into memory.
```{.python .input}
#@tab pytorch
y = torch.zeros(4)
torch.save([x, y],'x-files')
x2, y2 = torch.load('x-files')
(x2, y2)
```
We can even write and read a dictionary that maps
from strings to tensors.
This is convenient when we want
to read or write all the weights in a model.
```{.python .input}
#@tab pytorch
mydict = {'x': x, 'y': y}
torch.save(mydict, 'mydict')
mydict2 = torch.load('mydict')
mydict2
```
## Loading and Saving Model Parameters
Saving individual weight vectors (or other tensors) is useful,
but it gets very tedious if we want to save
(and later load) an entire model.
After all, we might have hundreds of
parameter groups sprinkled throughout.
For this reason the deep learning framework provides built-in functionalities
to load and save entire networks.
An important detail to note is that this
saves model *parameters* and not the entire model.
For example, if we have a 3-layer MLP,
we need to specify the architecture separately.
The reason for this is that the models themselves can contain arbitrary code,
hence they cannot be serialized as naturally.
Thus, in order to reinstate a model, we need
to generate the architecture in code
and then load the parameters from disk.
Let us start with our familiar MLP.
```{.python .input}
#@tab pytorch
class MLP(nn.Module):
    def __init__(self):
        super().__init__()
        self.hidden = nn.Linear(20, 256)
        self.output = nn.Linear(256, 10)
    def forward(self, x):
        return self.output(F.relu(self.hidden(x)))
net = MLP()
X = torch.randn(size=(2, 20))
Y = net(X)
```
Next, we store the parameters of the model as a file with the name "mlp.params".
```{.python .input}
#@tab pytorch
torch.save(net.state_dict(), 'mlp.params')
```
To recover the model, we instantiate a clone
of the original MLP model.
Instead of randomly initializing the model parameters,
we read the parameters stored in the file directly.
```{.python .input}
#@tab pytorch
clone = MLP()
clone.load_state_dict(torch.load("mlp.params"))
clone.eval()
```
Since both instances have the same model parameters,
the computational result of the same input `X` should be the same.
Let us verify this.
```{.python .input}
#@tab pytorch
Y_clone = clone(X)
Y_clone == Y
```
## Summary
* The `save` and `load` functions can be used to perform file I/O for tensor objects.
* We can save and load the entire sets of parameters for a network via a parameter dictionary.
* Saving the architecture has to be done in code rather than in parameters.
## Exercises
1. Even if there is no need to deploy trained models to a different device, what are the practical benefits of storing model parameters?
1. Assume that we want to reuse only parts of a network to be incorporated into a network of a different architecture. How would you go about using, say the first two layers from a previous network in a new network?
1. How would you go about saving the network architecture and parameters? What restrictions would you impose on the architecture?
:begin_tab:`mxnet`
[Discussions](https://discuss.d2l.ai/t/60)
:end_tab:
:begin_tab:`pytorch`
[Discussions](https://discuss.d2l.ai/t/61)
:end_tab:
:begin_tab:`tensorflow`
[Discussions](https://discuss.d2l.ai/t/327)
:end_tab: