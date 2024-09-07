---
layout: post
title: Learning a bit advanced Pytorch
---

## Learning a bit advanced Pytorch

### Training Loop demystified
* **Forward Pass**: Compute predictions (The code where you pass the input to the model to get the output)
* **Loss Calculation**: Compute the loss (The code where you calculate the loss between the predicted output and the target output)
* **Backward Pass**: Compute the gradients for all the parameters where we have requires_grad = True and is stored in the .grad attribute of the parameter (The code where you calculate the gradients of the loss with respect to the model parameters). In the loss.backward() function, it does not update the .grad attribute of the parameter. It just computes the gradient and stores it in the .grad attribute of the parameter.
* **Parameter Update aka optimization**: Update the parameters of the model for which we have .grad attribute / requires grad attributes (The code where you update the parameters using the gradients and a learning rate)
* **Zero_grad()**: The default behavior of the .grad attribute is to accumulate the gradients of the loss with respect to the parameters (The .grad is a tensor and it accumulates the grad for all the parameters). So we need to set it to zero before doing the backward pass.


### Training Loop in Pytorch
```python
for epoch in range(num_epochs):
    for i, (images, labels) in enumerate(train_loader):     
        # Will explain later
        optimizer.zero_grad()
        # Forward pass
        outputs = model(images)
        loss = criterion(outputs, labels)

        # Backward pass (calculate the gradients and stored in .grad attribute of the parameter)
        loss.backward()

        # Updates these parameters based on the defined optimizer and learning rate
        optimizer.step()
```



####  The alias codes and removing the abstraction 

`loss.backward()` translates to  
```
for param in model.parameters():
    if param.requires_grad:
        param.grad = Autograd.backward(loss, param)

```

`Optimizer.step()` translates to 
```
for param in model.parameters():
    if param.grad:
        param.data = param.data - learning_rate * param.grad

```

`optimizer.zero_grad()` translates to 
```
for param in model.parameters():
    if param.requires_grad:
        param.grad = None
```
