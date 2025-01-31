---
layout: post
title: Async Programming
date: 2025-01-02
---


[Google doc link](https://docs.google.com/document/d/1gMVzz5Haivst864_JZKWwY_AiNvu6pxMpttg2-dJopk/edit?usp=sharing)
[Async Programming](https://www.blog.pythonlibrary.org/2016/07/26/python-3-an-intro-to-asyncio/)
[]()

# Basics of Async Programming 

At any single time, a single CPU thread executes only a single function ( no multiprocessing happens ) atleast in the case of python !! Its just smart switching 

1. Pick up a event loop / create a event loop
2. Create / Add tasks in it 
3. Check for the status and if done return the result 

## 



## Coroutines : 
A coroutine is a special function that can give up control to its caller without losing its state. 

* Who's the caller here? 
* Event loop 

Functions that can suspend the execution and retain there state variable and resume back 

`yield` statement 

`yield <output>` outputs value to a function willing to accept it using yield statement
`output = yield` function that waits for input to come and till then gets suspended 

It stores the local variable in the `<coroutine_obj>.gi_frame.f_locals` here we can see the states in a dict format !


## Future

Task is a subclass of future ! 
A Future is an object that represents the result of an asynchronous operation that hasn't completed yet. Its a promise that something will happen in future 

Think of a Future as a pizza order receipt
* Pending: You've ordered but it's not ready.
* Done: Pizza is ready, and you can pick it up.
* Cancelled: You decided to cancel the order.

## Task 
When the future has started to run then its called a task.
Directly schedule a task using this async method 

### How chatGPT answers Streaming response

```python 
import time, string

def llm_output():
  time.sleep(1)
  val =''.join(random.choices(string.ascii_lowercase, k=15))

  # val = random.random()
  return f"Tokens-{val}"

def generate():
  while True:
    output = llm_output() #passing to UI
    yield output #produces output     

gen = generate()

def response():
  isEnd=0
  while isEnd != 1:
    value = yield #tuple
    print(value)
  pass

res = response()
next(gen)
next(res)

while True:
  output_tok = next(gen)
  res.send(output_tok) 
```

### Generator :
Generates output, so a function that periodically generates output 

```python
def _generator():
  print("Generator, ")
  while True:
    yield "Generates Final"

gen = _generator()
next(_gen)
```

### Receiver
Receiver input, that receives the input

```python
def _receiver():
  print("Receiver, it takes the data")
  value = yield

recv = _receiver()
recv.send("Value-1")
```















