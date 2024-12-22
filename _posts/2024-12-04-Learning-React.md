---
layout: post
title: Learning basics of React  
---


Doc link : https://docs.google.com/document/d/1Bg43BoC0xSmXugYI7L27NJm4ZFUaHDYlVYsFiTiodTM/edit?usp=sharing 


REPLIT : https://replit.com/@mohitdulani1/eg 

Trying to Learn React once again 
Delta to learn react is high, you need JS, css, html 

Importing / Exporting  
Named export ( export function App ) 
Default export ( export default <name> )

Default import ( import App from ‘./App’ )
Named import ( import {App} from ‘./App’ )  the { } must match the function name exactly 


Components :
different parts 
Like parts of a motorcycle , fan .. these are components and a site is made up many such components  
Component name should always start with a Capital letter
Inside JSX, we can write javascript also 
Can only return only one parent element 

Curly braces 
Inside curly braces, we can pass string , number and also for styling we can pass inside a js object inside {} so its {{ }}

Props 
Passing to a jsx tag: Props are the information that you pass to a JSX tag
Passing to a component: <Component prop1 = {100} prop2 = {{name:’mohit’}}>
 
Receiving / Read props Way-1 : function Component ({ prop1 , prop2 }) { // prop1 and prop2  }
Object passing needs to be wrapped in double curly braces

Reading props Way-2 : function Component (props) read as props.prop1 and props.prop2

Child prop (passing other component as a prop, content inside a prop) : The content inside the element acts as a prop

Key prop (inbuilt keyword in prop) : used to identify one object from another 


Template literals 
Passing in a combination of backticks + string + some dynamic value using $
** ` Hello ${Name} `


Rendering
Going from code to beautiful frontend  using VDOM , virtual dom
DOM is a tree like hierarchy  
State changed ? First updates virtual dom 
Then uses diffing to find changes in real dom to virtual dom
Then updates few nodes in the real dom ( Reconciliation ) 

Event Handling
https://youtu.be/wIyHSOugGGw?feature=shared&t=278 
Handling user interaction 
User clicking somewhere and the desired results is rendered using the event handler 
Event handler functions:
Are usually defined inside your components.
Have names that start with ‘handle’, followed by the name of the event.
Event handler props convention is to start with ‘on’ 

Event propagation:
Each event clicks finds its location in a tree and from there it calls all the events above it to the top node of the tree. 
Stopping propagation, Event handlers receive an event object as their only argument. By convention, it’s usually called e, which stands for “event”. 
e.stopPropagation() → to stop up the propagation of e to the parent node 
Frequently used : onClick
onChange
onSubmit 


State
useState(initial_state)
useReducer() 

Hooks
These can be called only at the top level of the component  
1. State Hooks
useState()
useReducer() 

2. Context Hooks
useContext()

3. Ref Hooks
useRef()

4. Effect Hooks
useEffect() : Runs once a component is rendered and you tell it to look for changes by providing dependencies. 

Setup code [ that performs something ] 
Use for everything that is non react like Calling an external API , external JS library , DOM event and we need to define when / how to call it , 



5. Performance Hooks ( not required in after react - 19 ) 
useMemo()
useCallback()

Purity
Same input should have same output and to always maintain this we can pass something called as <StrictMode>

Effects
Code that reaches outside react apps and calls other API’s

Context and useContext
Use context lets to read and subscribe to context created using create-Context
useContext >> is used when you dont want to pass on the data using props.. 
You can wrap the component inside the context provider and then use that component. 
   


Portals



Suspense 


Arrow function:
data.then((data) => console.log(data))
data.then((data) => {
   console.log(data)
})

Async arrow function 
data.then(async () => { })


Normal function:
function resolveIt(data){
   console.log(data)
}

data.then(resolveIt)


Fetching Data from API 
Using the fetch library / method from javascript 
But fetch is a asynchronous function and returns a promise you need to resolve the promise using .then() and .catch()

When you call a async function you gets a promise rather than the data … so you need to resolve that promise and if you need that API to be called and get resolved everytime to happen everything directly call it and resolve it ,.... 

 
UseEffect
For declaring / defining async functions, inside hook, the async function must be declared inside the scop and also called immediately ..

Do the desired roles what a function requires 
Then return a cleanup function 
Then [ ] to look for new changes 
 


==== 

Points to remember 

1_ The hooks should be declared inside the component as the components can be used at multiple places so making that global makes no sense .. 

2_ Props are read only, take the prop declare a state and then play with that state … its like this because of pure in react 

3_ react strictmode sometimes causes the component to render twice to check for its correctness .. this may be the reason of multiple renders that you see 

