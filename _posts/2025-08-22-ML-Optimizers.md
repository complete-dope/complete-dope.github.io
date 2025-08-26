---
layout : post
date : 2025-08-22
title : Deep learning Optimizers
---

[Gradients visualised](https://www.youtube.com/watch?v=7JEWlfFoJJQ)
[Second order derivative](https://course.ece.cmu.edu/~ece739/lectures/18739-2020-spring-lecture-08-second-order.pdf)

# Maths behind 
## Single variable
Things are very simple in single variable

Function definition : `f(x) = x^2`  
First derivative : `f'(x) = 2x`   
Second derivative : `f''(x) = 2` 

To find the Minima in single variable the f'(x) = 0 , and f''(x) >= 0 , these 2 conditions are enough to find minima 

## Multivariable /Multivariate 
First Derivative : This becomes a vector and is no longer a number 
Second Derivative : This becomes a matrix that is called Hessian  

So we cant just take sign of second derivative and tell maxima and minima ( what does sign of a matrix means ? nothing )

### FIRST DERIVATIVE 
In higher dim , The rate of change depends on location as well as  direction (bit obvious) 

Take this image and a point on it , and see how each direction has different gradient here so we need to find directional gradients here 

<img width="687" height="583" alt="image" src="https://github.com/user-attachments/assets/10fd3e9e-7891-490a-b651-4492c27ad4c0" />

But how to find it ? 

For any point on the curve , we can draw a plane along that cross section and then make it 1d and find its derivative   
See this image :   
<img width="759" height="425" alt="image" src="https://github.com/user-attachments/assets/9fbf9bcb-fa62-41cf-9d8d-63ddef80d047" />

But why cant we use our basic : 
`Dv​f(x)=h→0lim​hf(x+hv)−f(x)​`  
this formula to find the gradient ? 

We can use this and in fact its used also !!

Using the above formula: 
Partial derivative: 
f(x,y) = x^2 + y^2 + xy

Partial derivative in x-direction : f'(x,y) = means along y=0 (in all other directions its 0),  
`f(x,y) = x^2`
`f'(x) = 2x`

similarly partial derivative in y-direcion : means x=0 along curve ( all other variables are 0 there)
`f(x,y) = y^2`
`f'(x,y) = 2y`


Partial derivative in x-direction mean its same as the cross-section / plane drawn that intercepts all others at origin ( zero value ) , draw that cross section adnd take derivative along that curve

<img width="1066" height="693" alt="image" src="https://github.com/user-attachments/assets/1111a677-66aa-4877-9683-6ad77726d2f6" />


And now assume we want to approximate a point close to the origin the direction of partial derivative that is, f_pde(x,0) is a curve , now f_pde'(x,0) is a line / tangent to that curve at that point , we can easily find that point using the equation of a line `y = mx + c`

<img width="937" height="639" alt="image" src="https://github.com/user-attachments/assets/64650841-ac3d-4eb5-b95e-fcada4c57f2e" />

Now lets say we want to find derivative in a direction, that direction is some arbitrary , not regular direction (x,y,z) direction, then its 
<img width="902" height="464" alt="image" src="https://github.com/user-attachments/assets/451cd1a7-d855-4041-b23e-504b21ba17e9" />


Here the derivative of the curve is a line , and we get that by taking first derivative, that is,  And the calculations for the same go as this 
<img width="1518" height="459" alt="image" src="https://github.com/user-attachments/assets/7dc71902-b495-4159-a33d-e98795b84d68" />

So to get derivative , first derivative in higher dimensions we used the above formula 

### SECOND DERIVATIVE

1st derivative is already a line , we just need to find its slope to get the 2nd derivative 
So find the 

<img width="3952" height="1884" alt="image" src="https://github.com/user-attachments/assets/4e127533-d08c-43a7-93af-d96423d46028" />


Okay what if we need that in a direction , that is also sorted we know how to do directional derivative right ? 

`f(h,2h) - f(0,0) / root(5 * h^2)` 

<img width="1332" height="719" alt="image" src="https://github.com/user-attachments/assets/777c8790-a5db-4107-92e5-8ae9c0756a35" />

The calculation is very simple same as we did for the first one , we already now know how to take points on the line , that is, so same using directional derivativees for the second derivative that is done ! 
 

<img width="970" height="709" alt="image" src="https://github.com/user-attachments/assets/3b97ff30-8605-450e-8b7e-63fa758100bb" />

### Taylor series 
It presenta a beautiful way of approximating functions, for any complex function for which you dont know its expansion we can approximate that function for some value to help us solve it .. 

Take for example cos(theta) , its taylor approximation comes out as : ( 1 - (theta**theta)/2 ) 

<img width="1000" height="669" alt="image" src="https://github.com/user-attachments/assets/4b1b2240-c05c-42c0-aa72-49dd28764991" />



### Newton method 

[Newton Method in Optimisation](https://www.youtube.com/watch?v=W7S94pq5Xuo)  

In first derivative we approximate the descent as : `f'(x) = f(x) - f(x_k) / (x - x_k)` , this 
To refine our approximations, we use [taylor series](https://www.youtube.com/watch?v=3d6DsjIBzJ4) , 


# DL Optimizers 

## SGD ( Stochastic Gradient Descent ) 
This is very simple / basic optimasation algorithm that takes in account almost nothing and treats each parameter as equal :   
`Theta_t+1 = Theta_t - (learning_rate) * (dL / d(Theta_t))`

It uses single derivative to solve the optimisation problem 
What is  `dl/d_theta` is zero ? this could also mean the model is in local maxima or minima 

In high dim , ML problems are extremely rare , most critical points are saddle points, 

Disadvantages : 
1. All params have same learning rate
2. Every parameter gets updated with same step-size 

## AdaGrad
Adaptive Gradient : Its adapts the learning rate for each feature depending on its sum of product of previous gradients , it tends to assign higher learning rates to infrequent features which ensures the parameter updates rely less on freq. and more on relevance 

Square of anything tells us how big was that thing, irrespective of the sign , a -10 squared gives us 100 , that tells us that -10 was a large value in first place. Similarly,
`-2 --> squared --> 4` : tells that the number itself was small 

> Gradient square (G_t ^ 2) in itself doesn't mean anything its just tells us the magnitude.

If the Sum( g_t @ g_t.T ) is higher, that means this parameter was seeing some higher gradients, and we need to slow it down a bit 

If the Sum( g_t @ g_t.T ) is lower, that means this parameter was seeing lower gradients, and we need to increaase its learning rate a bit

So its an inverse relation, 
`learning_rate_new = learning_rate_old / Sq_root(Sum(G_T))`

<img width="1200" height="385" alt="image" src="https://github.com/user-attachments/assets/e1b42718-4391-455e-ab8e-a54e0ecadedb" />

Disadvantages: 

1. Its sensitive to the initial conditions , if the initial gradients are larger the learning rates will be lower that means that param will be taking up small steps that will eventually lead to settling in some local minima so we need to avoid that ... 

## AdaDelta 

<img width="219" height="27" alt="image" src="https://github.com/user-attachments/assets/57f2322b-7122-4adc-812d-f96d80e036bb" />

Adadelta tackles this problem by doing 'WEIGHTED AVERAGE' of the sum of prev term and the current gradient value and the `rho` here is a hyper-parameter known as decay rate .. 


## SGD with momentum 
The formula is quite simple just we are taking momentum to go in a particular direction nothing more !! 

<img width="740" height="752" alt="image" src="https://github.com/user-attachments/assets/8b9de4f7-5eaa-4d91-a533-d1f09b1d0513" />

Nesterov said 
rather than taking the gradient at current step , go to the step where momentum is pushing and take gradient from that step,  that way you already capture the next incoming information as well 

So you adjust early and converge faster and not wait till the end-moment

## RMSProp 
Developed by Geoffrey Hinton, 

* Adagrad takes in previous muliplication of weights and then weighs the learning rate based on the prev steps

So if the previous weights are higher, the learning rate decreases and eventually the leads to vanishing grads 

To avoid this in Adagrad, in RMS prop we use EMA ( estimated moving average ) 

Here, EMA is the estimated moving average, `EMA_t = alpha * X_t + (1-alpha) * EMA_t-1`

So we just replace the G_t here with WMA with EMA

## Adam 
[Adam Optimizer Cornell](https://optimization.cbe.cornell.edu/index.php?title=Adam)   
TODO : READ THE MATHS BEHIND THE PAPER AND HOW THEY ARE SOLVING IT !! 
Adaptive moment optimisation 
This uses optimisations of the first and second moments of the gradients to adapt the learning rate for each weight of the neural net. 
Its requires only first order gradients wghere memory requirement is too little, 


The concept is very simple, the (G_t ^ 2) tells the its magnitude of the gradient, that is, how large the gradient was at first place and we take EMA that is taking some parts from prev.  calculation and some from the current one and we take 2 moments first one is for the momentum calculation and second one for regularising the learning rate ( learning_rate / Square_root(v_t)), and the first moment so that tells us the vector, the direction (g_t) of the step and (v_t) tells us the magnitude of the Grads  

<img width="2648" height="1546" alt="image" src="https://github.com/user-attachments/assets/28b3b9a8-613c-45ea-bd2c-2b891ec1640e" />

The formula is same for momentum + adagrad and that works just great !! 


## AdamW 
Researchers add L2 regularization to the loss function, when multiplied with the normalisation factor (normalization of learning rate) that loses its effect so to avoid this thing, we seperate out the step, we apply L2 regularisation after that step 

Adam with L2 regularisation : 
<img width="887" height="479" alt="image" src="https://github.com/user-attachments/assets/66b35f05-8d79-4872-bbfd-ba3ce404cc3f" />

The same term is now added at the last just with the full learning rate rather than normalised  
<img width="1058" height="619" alt="image" src="https://github.com/user-attachments/assets/7b3a3fc6-4170-420f-b3a9-c13036534511" />

## LARS / LAMB 
[LARS PAPER](https://arxiv.org/pdf/1904.00962) 

Uses 2nd order derivatives 


















