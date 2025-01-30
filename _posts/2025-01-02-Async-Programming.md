---
layout: post
title: Async Programming
date: 2025-01-02
---


[Google doc link](https://docs.google.com/document/d/1gMVzz5Haivst864_JZKWwY_AiNvu6pxMpttg2-dJopk/edit?usp=sharing)
[Async Programming](https://www.blog.pythonlibrary.org/2016/07/26/python-3-an-intro-to-asyncio/)
[]()

# Basics of Async Programming 

## 

## Coroutines : 
Functions that can suspend the execution and retain there state variable and resume back 

`yield` statement 

`yield <output>` outputs value to a function willing to accept it using yield statement
`output = yield` function that waits for input to come and till then gets suspended 

It stores the local variable in the `<coroutine_obj>.gi_frame.f_locals` here we can see the states in a dict format !


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


