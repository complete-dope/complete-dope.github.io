---
layout: post
title: Learning TypeScript
date : 2025-02-30
---

[Typescript](https://www.youtube.com/watch?v=BCg4U1FzODs)

# Intro and Setup for Typescript

Superset of Javascript, its built on top of JS 

JS is a dynamically typed language, where we dont define the types and they are associated with run-time also like python
whereas,
TypeScript is a statically typed language, you define types to variable like , C , java 

You need to compile Typescript to work for your case, it compiles .ts to .js and   

## Learning typescript 

```javascript

let id = 5; // js
let id: number = 5; // typescript

```
Here we defined a type and as the modern browsers can only understand JS and no this fancy languages so we need to compile this to JS. 

To convert to JS we use `tsc`, that is typescript compiler 

`tsc index.ts` : This compiles the index.tsc file to index.js file 

Create at typescript config file, using `tsc --init` 

This creates a file named `tsconfig.json`, that contains all the confs for your .ts file, where you mention the root directory , the source directory , javascript version to compile to .. etc 

`tsc --watch` : watches for all tsc files and auto compiles them in the destination directory mentioned 



## Data-Types and Usage in Typescript 

```javascript

// All PRIMITIVE TYPES in typescript 

// string: Textual data (e.g., "hello").

// number: Numeric values (integer, float, hexadecimal, etc.).

// boolean: true or false.

// null: Explicit absence of a value.

// undefined: Variable not yet assigned.

// symbol: Unique, immutable identifier (e.g., Symbol('key')).

// bigint: Large integers (e.g., 100n).


// All SPECIAL TYPES in typescript

// any: Opt-out of type checking (use sparingly).

// unknown: Type-safe counterpart of any (requires type assertion before use).

// never: Represents unreachable code (e.g., function that always throws an error).

// void: Absence of a return value (common in functions, e.g., function log(): void).


let id: number = 5;
let company: string = "Traversy Media";
let isPublished: boolean = true;
let x: any = "Hello";
x = true;


let age: number
age = 50;


// Array of numbers
let ids: number[] = [1, 2, 3, 4, 5]; // ids should be a list of numbers / integers

// Array of any
let arr: any[] = [1, true, "Hello", 4, 5];


// Number , String , Boolean (tuple of 3 data types)
let user: [number, string, boolean] = [1, "Traversy", true];
let person: [number , string, boolean] = [1, "brad", true];


// Array of tuples of number and string   
let employee: [number, string][] 
employee = [
    [1, 'hello'],
    [2, 'world'],
]

// Union
let pid: string | number

pid = "12";
pid = 22;  

// Enum 
enum Direction1{
    Up, 
    Down, 
    Left, 
    Right
}

enum Direction2{
    Up = "Up", 
    Down = "Down", 
    Left = "Left", 
    Right = "Right"
}

// by default the values are 0, 1, 2, 3 in the order !! 

console.log(Direction1.Up); // 0
console.log(Direction1.Down); // 1
console.log(Direction1.Left); // 2


console.log(Direction2.Up); // Up
console.log(Direction2.Down); // Down
console.log(Direction2.Left); // Left

// Objects (key-value pair) (key-name : data-type )
type User = {
    id: number,
    name: string
}

const user2: User = {
    id: 1,
    name: "John"
}

```
















