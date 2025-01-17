---
layout: post
date: 
title : Learning how web works and building my custom DOM for it !! 
---

[DOM Introduction](https://www.w3.org/TR/REC-DOM-Level-1/introduction.html)

# DOM
#### Understanding this line `The Document Object Model (DOM) is an application programming interface (API) for HTML and XML documents. `

DOM ( Document Object Model )
The DOM is like a map of a webpage or document. Imagine a webpage (HTML) as a tree where each part—like headings, paragraphs, buttons, or images—is a branch or a leaf. The DOM is the structure of this tree that makes it easy for programs to understand and interact with the webpage.

![Dom Tree](https://www.w3.org/TR/REC-DOM-Level-1/images/table.gif)

API 
An API is code that allows a program to "talk to" something else. In this case, the DOM API provides tools for programmers to interact with a webpage's structure.

Understanding it all, 
DOM is a "map" of a webpage or document. It provides a way (using an API) for programmers to interact with and manipulate the webpage's structure, content, and style.


Before the DOM, different browsers handled webpages in slightly different ways, making it hard to write programs that worked everywhere.

[DOM customs web browser's , mock web engines must be based on](https://www.w3.org/TR/REC-DOM-Level-1/level-one-core.html)
[Custom DOM implementation](https://github.com/browser-use/browser-use/blob/main/browser_use/dom/buildDomTree.js)

## What is xpath ? (XML path language) 
The absolute path of the node / which element to interact with , the absolute path of the node 

Example include: 

```xpath
html/body/div[3]
html/body/c-wiz[2]/div/div[2]/c-wiz/div/c-wiz/c-data
```

These start from the root html , till the absolute end of the node name 

The DOM is created by browsers , browser have a standard on how to create a DOM , the xpath is a way to interact with the DOM in an efficient way  

## Custom DOM 

Features of using a custom DOM , 
add features like is_clickable , is_visible etc .. 


## The flow goes like

1. Creates all JS interactable tags from the custom DOM. 
2. Pass to the LLM model, and ask it to define the next step / where to click from there
3. Make bounding boxes using the core Algo, and then add labels to that , the labels should be same as what you got from the custom DOM parsing
4. Pass that to a good VLM model and ask it to find the changes it did ..       








