---
title: FAQ for PyTorch
tags:
  - Knowledge
---
## Error: RuntimeError: Trying to resize storage that is not resizable

The shapes of different data are not the same, so they cannot be alligned or collated correctly.

## What is the shape for different loss functions?
The shape of the input and target for the loss function is very annoying. So I summarize them here.

### CrossEntropyLoss

1. shape
```
predictions = torch.rand(2, 3, 4)
target = torch.rand(2, 3)
print(predictions.shape)
print(target.shape)
nn.CrossEntropyLoss(predictions.transpose(1, 2), target)  # the shape should be transposed!
```
2. type

`RuntimeError: Expected object of scalar type Long but got scalar type Float for argument #2 'target'`

`input` can be in any format, just `targets` should be in `long`.

```
# Example of target with class indices
loss = nn.CrossEntropyLoss()
input = torch.randn(3, 5, requires_grad=True)
target = torch.empty(3, dtype=torch.long).random_(5)  # target should be long
output = loss(input, target)
output.backward()

# Example of target with class probabilities
input = torch.randn(3, 5, requires_grad=True)
target = torch.randn(3, 5).softmax(dim=1)  # target with probabilities should be converted to between [0,1].
output = loss(input, target)
output.backward()
```

### NLLLoss


### Dice loss
Because I used the  `monai.DiceLoss`, the shape should be


### error: TypeError: only integer tensors of a single element can be converted to an index
Answer: change `x` to `torch.tensor(x)`



