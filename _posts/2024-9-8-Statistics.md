---
layout: post
title: "Statistics for ML"
date: 2024-09-08
---

## I will deep dive into the whole required stastistics , that would be a required to learn stable diffusion from the very scratch


### Entropy [Link](https://www.youtube.com/watch?v=2s3aJfRr9gE)

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


### Cross-Entropy ( not yet intutive , need to research more on it )

No. of bits required to represent or transmit an average event from one distribution compared to another distribution is called Cross-Entropy

p : target distribution
q : another distribution

H(p,q) = - sum ( P(x) * log(Q(x)) )


### KL-Divergence ( once you understand the above two concepts , this is very easy ) 

Cross entropy = KL-Divergence + Entropy 


