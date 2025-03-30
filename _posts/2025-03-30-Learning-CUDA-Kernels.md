---
layout: post
date: 2025-03-30
title: Learning and Making CUDA kernels as a future skill 
---

## THIS IS A SKILL OF FUTURE 
[CUDA DOCS](https://docs.nvidia.com/cuda/cuda-c-programming-guide/)


## Terminologies : 
Warp : grp of 32 threads scheduled and working on the same streaming multiprocessor 
SIMT : single instruction , multiple threads
Lockstep : all threads starts in parallel / works at the same time  
SM : Streaming Multiprocessor ( CPU aka processor , single processor , useful for all tasks ... whereas .. gpu only for intensive application handed over to it by cpu )
Stream : like event loop in CPU used for cuda async operations  
PTX : parallel thread executions , has a seperate ISA used for cuda code and runs on GPU 

## Structure of GPU :



## Memory in GPU : 

* Shared Memory : This is used by all threads in a block and is assesible using `__shared__` keyword  
* Global Memory : This is the default memory accessible by all kernels `cudaMalloc` , `cudaMemcpy`  
* L1 cache : This is hardware managed memory, like a CDN, the most frequently used memory is placed close to the blocks ( can't be programmed )  
* L2 cache : This is hardware managed memory and cant be programmed like L1

Yes, shared memory is different from L1 and L2 cache, and you can explicitly use shared memory in your CUDA programs, but L1 and L2 caches are hardware-managed and cannot be directly controlled.

Serial Code : Synchronous code , that runs sequentially on the CPU 
Parallel Code : Code that runs sequentially on the GPU

### SIMT Model 
So this model assumes that the threads have same instruction and they are working on different data .. and thread role divergence is not assumed !! as this helps in executing in parallel at the same time and a warp scheduler is used to schedule it and works in lockstep 

Warp divergence: If the code depends on threadIdx , then we cant do warp divergence as now we have multiple instructions and this reduces parallelism ...

```python
# warp_divergent.cu
__global__ void divergent(){
  int idx = threadIdx.x;
  if (idx % 2 == 0){
    s[idx] = 2;
  }
  else{
    s[idx] = 1;
  }
}


# warp_scheduled.cu
__global__ void divergent(){
  int idx = threadIdx.x;
  int data;
  if (idx % 2 == 0){
    data = 2;
  }
  else{
    data = 1;
  }
  s[idx] = data;
}

```
### Async programming
Streams are like event loop , schedules async programs and have access to stop and start them !!
can have multiple streams (as its a multiprocessor with multicores )  



## Compilation and low level stuff in the API 
CPU COMPILATION HAPPENS AS : 

```
Source code > compiler > asm file
asm file > assembler > object file
object file > linker > exe binary 
```

What currently happens in software is the above steps gets followed for langs like C / C++ for high level languages like python, Java , Javascript they get converted to intermediate file format like .pyc   



`nvcc compiler` : based on backend powered by LLVM , 
seperates device and host code , 
converts device code to PTX (assembly code) 
converts host code to obj file 

JIT compilation: 
GPU driver takes in the PTX code that is generated in the compilation step by nvcc 
the conversion to binary happens by the gpu drivers which is not open-sourced proprietary software (nouveau is open sourced and does a decent job)
























