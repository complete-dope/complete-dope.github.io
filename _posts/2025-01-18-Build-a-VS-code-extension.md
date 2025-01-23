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

## After all this initialisations what next to do ? 

## Webview
Everything that we see in a vs code extension is built out in a webview ( a single extension can only have a single webview ) , 
That webview is can be built in HTML , css , JS or using some framework like React, Angular, Vue JS .. 

In the webview initialise a react / typescript project and code it, the directory will be '/src/components/'  


## Interacting with webview 
For the webview to interact with the backend code, the vscode.postMessage with a type {"<>"} (posting the event), the event needs to be posted so that means we need to use switch-case for that to work ...


## BASIC FLOW FOR AN EXTENSION 

`package.json` : tell the command that you are going to develop

`extension.js` : register that same command and tell in the function what you want it to do 


## FLOW FOR AN EXTENSION 

UI has the buttons, textarea , dropdowns , etc .. 
The user interact with these values and these values are linked to the 'postMessage' .. the interactions with the frontend are sent to the backend i.e. extension using the post Message ( kind of a post request )  

`package.json` : the commands name for the extension (register command / webview). In package.json we register the commands name that the project has with the description of what it does  ( like the endpoint declaration )   

`extension.js` : In this we register the command mentioned in package.json and tell the functionality of that command, 

webview.onDidReceiveMessage() , this takes in the data and classifies using switch-case to tell what to do .. 



## Typescript 
Interface in React = enum in python 


















