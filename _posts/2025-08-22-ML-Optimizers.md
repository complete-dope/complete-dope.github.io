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


And the calculations for the same go as this : 
<img width="1518" height="459" alt="image" src="https://github.com/user-attachments/assets/7dc71902-b495-4159-a33d-e98795b84d68" />

So to get derivative , first derivative in higher dimensions we used the above formula 

### SECOND DERIVATIVE

1st derivative is already a line , we just need to find its slope to get the 2nd derivative 
So find the 

<img width="3952" height="1884" alt="image" src="https://github.com/user-attachments/assets/4e127533-d08c-43a7-93af-d96423d46028" />


Okay what if we need that in a direction , that is also sorted we know how to do directional derivative right ? 

`f(h,2h) - f(0,0) / root(5 * h^2)` 

<img width="1332" height="719" alt="image" src="https://github.com/user-attachments/assets/777c8790-a5db-4107-92e5-8ae9c0756a35" />

The calculattion is very simple same as we did for the first one , 

<img width="970" height="709" alt="image" src="https://github.com/user-attachments/assets/3b97ff30-8605-450e-8b7e-63fa758100bb" />



## SGD ( Stochastic Gradient Descent ) 




## AdaGrad
Adaptive Gradient : Each param has its own learning rate depending on how its behaving in previous steps 



## Adam



