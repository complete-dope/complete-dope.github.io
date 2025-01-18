---
layout: post
date: 2025-01-18
title: Building a VS code extension
---

[starter](https://www.youtube.com/watch?v=q5V4T3o3CXE)
[basics of node and npm](https://youtu.be/P3aKRdUyr0s?)

# Basics of NPM and Node

NPM : Node package manager 
A collection of all the open source JS work that people from all over the world contribute to. It helps in simplifying your JS work as you dont have to write everything from scratch 

Nodejs : 
Javsascript runtime which does JIT compilation for JS , unlike python which uses cypthon for compiling code to C and some of it uses 

package.json : will list all the packages your project is using so if your project has package.json user can directly use it to install all of those packages 

# Building a VS code extension from scratch 

start with `npm install -g yo generator-code`

yo : yeoman , automates boiler plate project templates 
generator-code : to install vs code sample extensions using yo, so yo named this as generator-code

`extension.js` = This is the main entry point for your extension. Customize it to implement your extension's functionality.

It contains the code that runs when the extension gets activated inside a function called activate and runs at the first time ... 

Add the commands , add event listener , implement features like webview, status bar items etc 

`package.json` = dependencies , contribute commands ( which tells it where to route for a particular input ) 






