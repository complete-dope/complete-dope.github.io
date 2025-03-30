---
layout: post
date: 2025-03-30
title: Learning and Making CUDA kernels as a future skill 
---

## THIS IS A SKILL OF FUTURE 
[CUDA DOCS](https://docs.nvidia.com/cuda/cuda-c-programming-guide/)

Structure of GPU :



Memory in GPU : 

Shared Memory : This is used by all threads in a block and is assesible using `__shared__` keyword 
Global Memory : This is the default memory accessible by all kernels
L1 cache : This is hardware managed memory, like a CDN, the most frequently used memory is placed close to the blocks ( can't be programmed )   
L2 cache : This is hardware managed memory and cant be programmed like L1 


Yes, shared memory is different from L1 and L2 cache, and you can explicitly use shared memory in your CUDA programs, but L1 and L2 caches are hardware-managed and cannot be directly controlled.

