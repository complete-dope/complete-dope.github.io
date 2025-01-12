---
layout: post
title: "Machine Learning"
date: 2024-09-08
---

#### A medium level ML concepts 

Activations : 

In activation function, you might have seen we are kinda trying to avoid the negative values / trying to keep only a positive values or only negative values ..

Ex: ReLU    

What's the reason behind this and why are we ditching them?
Earlier the most common activation function used to be sigmoid and tanh but now most common ones are ReLU and its derivatives

The shift is because of the derivatives for these functions in the computation graph 

![Computation Graph](https://www.researchgate.net/profile/Yuqing-Chen-3/publication/344260274/figure/fig3/AS:936580785139716@1600309668673/A-a-neural-network-and-b-its-computational-graph-The-c-forward-and-backward.png)

  
The range of d(tanh) lies between 0 and 1, the multiplication of too many of these values lead to way less gradient values and the weights don't get updated properly 

0.8 * 0.8 * 0.8 *0.8 * 0.8 => 0.32 ( multiple's of these would lead to vanishing grads )

1) Can linear layer output more than the input that it took ?
* No that is not possible, as the weight initialisation are in rnage (-1 -- 1)

2) Why squishing/removing the negative values of the weights using the activation functions is important ?
* reason is vanishing gradients   


input -> linear -> tanh(x) -> linear -> tanh -> output 

Forward pass  
(x) -> ( wx + b ) -> (0.8) -> (wx + b) -> (0.8) -> output 

initial x=10: (10) -> (0.3*10 + 0.3 = 3.3) -> (0.8) -> (0.3 * 0.8 + 0.3 = 0.54) -> (0.4)
initial x=0.5: (0.5) -> (0.3*0.5 + 0.3           = 0.45) -> (0.3) -> (0.3 * 0.3 + 0.3 = 0.39) -> (0.25)


In the backward pass,   

Derivate: quantifies how sensitive a function is with respect to the change in its the input 

[Loss.backward()](https://discuss.pytorch.org/t/what-does-the-backward-function-do/9944) -> computes dloss/dx for all the parameters x , which has requires_grad in the model 

dL / dWs -> dL / d(wx+b) * d(wx+b) /        dx  
(Ws : all the parameters in the model) -> and is done using the chain rule  

Optimizer:  

Changes the weights of the model (according to the policy defined ) to minimize the loss function 

W_i+1 = W_i - lr * dL / dW_i 

(The sgd is not well explained in the pytorch docs , the loop they represent is teh whole training loop , not the sgd loop)

