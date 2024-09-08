---
layout: post
title: "Statistics for ML"
date: 2024-09-08
---

### Deep dive into the whole required stastistics , that would be a required to learn stable diffusion from the very scratch


#### Entropy [Link](https://www.youtube.com/watch?v=2s3aJfRr9gE)

This is best understood using examples
Assume 2 machines A and B , that produces coins ( A,B,C,D ) with some probability distribution.

The probability distribution of the coins produced by machine A is given by P(A), P(B), P(C), P(D)
The probability distribution of the coins produced by machine B is given by Q(A), Q(B), Q(C), Q(D)

P(A) = 0.25
P(B) = 0.25
P(C) = 0.25
P(D) = 0.25

Q(A) = 0.125
Q(B) = 0.125
Q(C) = 0.250
Q(D) = 0.500

And we are now playing with this machines A and B, 
we will push a button and machine will produce a coin and we have to guess that by asking minimum no of yes / no questions to the machine.

Lets play with Machine A

Machine A : 
shrrr ( coin produced is A )

The most efficient way to guess the coin produced is to ask questions based on the probability distribution of the machine A, ask questiosn whihc divide the probability distribution into two equal parts.
Q1) Is the coin produced is CD ?
No

Q2) Is the coin produced is B ?
No

*Means the coin produced is A*
At min. we asked 2 questions to the machine A to guess the coin produced.
On average we asked 2 questions to the machine A to guess the coin produced.


Lets play with Machine B

Machine B : 
shrrr ( coin produced is A )

*** Why are we not asking questions in pairs here? We could have asked questions like Is the coin produced is AB ? or Is the coin produced is CD ? ***  
This is asking question like is the coin produced CD will increase the no. of questions by more ... as we know half of the time the coin produced is D ... ( This is the only efficient way to ask questions )

Q1) Is the coin produced is D ?
No

Q2) Is the coin produced is C ?
No

Q3) Is the coin produced is B ?
No

*Means the coin produced is A*
At min. we asked 3 questions to the machine B to guess the coin produced.
On average we how many questions we need to ask to machine B ?? 
This cant be said as the probability distribution of the machine B is not uniform ... 


To understand this we need to understand this in analogous way, think we want to build Machine A and Machine B.

Machine A is the gold standard, it produces coins with the probability distribution P(A), P(B), P(C), P(D)

Take a peg and bounce disks
![Image.png](/images/stats_bouncing_peg_MachineA.png)

We need to make 2 levels as seen in the above image 


For the Machine B :  
![Image.png](/images/stats_bouncing_peg_MachineB.png)  
we need to make it to 3 levels 



Total no. of bounces can be calculated as weighted probability of the no. of bounces for each level.

Q(A) = 0.125
Q(B) = 0.125
Q(C) = 0.250
Q(D) = 0.500


Total no. of bounces = Q(D) * no_of_levels_down_D_is_present + Q(C) * no_of_levels_down_C_is_present + Q(B) * no_of_levels_down_B_is_present + Q(A) * no_of_levels_down_A_is_present  

Total no. of bounces = Q(D) * 1 + Q(C) * 2 + Q(B) * 3 + Q(A) * 3 

Total no. of bounces = 0.500 * 1 + 0.250 * 2 + 0.125 * 3 + 0.125 * 3 = 1.75


No. of bounces = No. of questiosn


Machine A requires 2 questions to guess the coin produced
Machine B requires 1.75 questions to guess the coin produced

Machine B produces less information hence less uncertainity (if a thing is more certain to happen we automatically have ask less information to confirm it irl )

this measure of Certainity is the called the `entropy` of the probability distribution

Entropy = - sum ( P(x) * No. of bounces ) [same as above formula]

more specifically no. of bounces are inversely proportional to the probability of that event occuring and that is 
= log(outcomes at that level)

= log(1/P(x))

which makes entropy =  sum ( P(x) * log(1/P(x)) )
or 
= - sum ( P(x) * log(P(x)) )

Entropy is the amount of information needed to describe the outcome of a random variable / remove the uncertainty of a random variable

In short, 
whenever the outcomes are equally probable entropy is high and if the outcomes are not equally probable entropy becomes low .. 
( not that much intuitive but just the math works !)


#### Cross-Entropy ( not yet intutive , need to research more on it )

Imagine we're trying to predict the weather for the next day in a certain city. For simplicity, let's say there are only three possible weather conditions: Sunny, Rainy, or Cloudy.

True Distribution (P):
Let's say based on historical data, the actual probabilities of these weather conditions are:

Sunny: 50% (0.5)
Rainy: 30% (0.3)
Cloudy: 20% (0.2)



This is our "true" distribution P.

Predicted Distribution (Q):
Now, suppose a meteorologist makes a prediction for tomorrow's weather:

Sunny: 40% (0.4)
Rainy: 35% (0.35)
Cloudy: 25% (0.25)


This is our predicted distribution Q.

Now, cross entropy tells us, If we use meterologist guesses to make predictions, how surprised will we be on average when we see the actual weather?

If the meterologist guesses are close to the actual distribution, cross entropy will be low because we'll be surprised less when we see the actual weather.
If the meterologist guesses are far from the actual distribution, cross entropy will be high because we'll be surprised more when we see the actual weather.

High suprise means more entropy and more no. of bits
As the units of suprise / entropy is bits 

If the event is more probable, then we require less information about it and vice versa  
so information of event = -log(px) 

Assume a case like this 

Q_ The true prob for a event x = 0.125 , the q(x) = 0.125 
then px * logqx = 0.125 ** 3 = 0.375

whereas 
px = 0.125 and qx = 0.500
then px * logqx = 0.125 * *1 = > 0.125

which means I am getting more surprised when the actual and predicted distribution are same compared to actaul and predicted are different ? 

A_ When the event with such low probability actually occurs, it gives more surprise and more no. of bits. When a more probable event occurs it gives less surprise hence less no. of bits.. but in the `summation` makes things even and the different prob. distributions gives more suprise 

*Case 1*: P matches Q  
P(x) = Q(x) = 0.125, P(not-x) = Q(not-x) = 0.875
Cross-entropy = -[0.125 * log₂(0.125) + 0.875 * log₂(0.875)] ≈ 0.544

*Case 2*: P differs from Q   
P(x) = 0.125, Q(x) = 0.500, P(not-x) = 0.875, Q(not-x) = 0.500
Cross-entropy = -[0.125 * log₂(0.500) + 0.875 * log₂(0.500)] = 1.000


#### KL-Divergence ( once you understand the above two concepts , this is very easy ) 

KL-Divergence = Cross entropy - Entropy 

Entropy: The inherent unpredictability of the weather in your area. Some places have more variable weather (high entropy) than others.

Cross-entropy: How surprised you are by the actual weather, based on your predictions. If your predictions are way off, you'll be very surprised (high cross-entropy).

KL Divergence: The extra surprise you experience because your predictions aren't perfect. It's how much more often you're caught without an umbrella (or with an unnecessary umbrella) compared to if you had perfect knowledge of the weather patterns.
        
