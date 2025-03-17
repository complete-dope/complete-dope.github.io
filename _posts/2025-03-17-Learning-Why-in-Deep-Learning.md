---
title : Learning the 'Why' in Deep Learning 
layout : post
date : 2025-03-17
---

https://claude.ai/share/82ba8ee9-f673-4f8a-a89a-9fd380bd0e53 

We all know about DL architectures, but do we know how researchers arrived at this !! 

## How to arrive at a deep learning architecture ? How to make connections between layers and be intuitionally correct ? 

The logic behind a deep learning architecture , how to make the gradients flow from different parameters space and still making sense , and the use of residual connections , layer normalisation .. etc 

Starting with vanilla attention network / transformer network 
Its has 6 boundaries / parameter space

1. Token embeddings (vocabulary → vector space)
2. Positional embeddings (position → vector space)
3. Attention projection matrices (Q,K,V)
4. Feed forward network layers
5. Layer normalisation params
6. Output Projection ( for next token prediction )

## How to make information flow and keep these spaces seperate 

Residual connections : Keeps the information flow while keeping the parameter space seperate ( HOW ) ? 

Layer Normalisation : Standardizes output between modules ,allowing each component to 

FFN : point wise transformation, meaning it treats each position independently. In contrast, attention mixes information across positions. 


## How does a single loss functions work for the whole network ?    

Loss function as single 'north star', that guides all the parameters toward a common goal. Gradient tell each parameters how it specifically contributed to the error. 


"Which direction should I change to help the overall goal ?"


## Residual connection 

The residual connections should not have normalisations in them , as there role is to provide a direct path for gradients to flow through the network . 
Adding normalisation in there will affect the gradient that is the flowing through it !!





























