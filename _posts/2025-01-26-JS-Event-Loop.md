---
layout: post
title: Learning JS Event Loop 
date: 2025-01-26
---

# Learning JS Event Loop

[Event loop](https://www.youtube.com/watch?v=cCOL7MC4Pl0)


Main thread : where every thing happens 
something on main thread, takes a long time ( 200ms ) that becomes noticeable to the users and is not user exp

The human body , is multithreaded in all ways , we can type , listen , understand , talk , move eyes , move lips ..etc all at the same time 


But only while sneezing, we become single threaded, we cant do nothing but sneeze 

so what we do is create multiple threads (networking thread , crypto thread , monitoring IO device etc ) and once they are done they have to combine back to the original-main thread

Event Loop is the one that orchestrates all of this !!

What would happen is lot of JS running parallel in many threads and all editing the same DOM , and you end up with all these race conditions 

so we queue the taks and run that in a step 

## Event loop
Runs around CPU in an efficient manner 


### Task Queue
When we queue a task, the event loop takes a detour, browser says to event loop I have got a job for you to run .. event loop says add it to my to-do list 

Only one task can be processed at a time, rest all the tasks get stacked up and wait for there chance to play  

To queue a task we can use `setTimeout` in JS  

The rendering calculation happens at the start of each frame , that includes style calculation , layout and paint  

### MicroTasks
associated with promise 

Browsers wanted to give developers a way to monitor DOM changes 
Using DOM we change the HTML in a programmatic way and all langs do that .. 


JS task:
If from some button click , an event got registered and that event initiated a microtask, then the JS will first finish task on stack, then call microtask then call next JS function ...   



















