---
title: Learning Vue
layout: post 
date: 2025-01-06
---

Setup : 

* CDN -> script tag and get started ( no installation required )

* Vue CLI -> old not recommended way

* Create Vue -> use vite and ecosystem of plugins and is the recommended way  


# Vue.js
Written by someone that loves python 

Its a Progressive JavaScript Framework ( PJF )

Progressive JavaScript Framework, means even if your project is React you can use vue.js for some parts / components of it rather than fixing on vue from start .. nice benefit 


SPA ( single page application ) is a web application that loads a single HTML page and dynamically updates the page as the user interacts with it. 

Reactive data binding means a magical flow when the data updates the UI also updates itself , no need to manually write the updation logic ( done using virtual DOM ) 

Component based architecture , everything is a component , you can reuse it anywhere in your project

## Vue components 

The actual file that has .vue as the extension is called a component


Components has this following structures .. 
```js
<script>
    // JavaScript code - logic
    data(){

    }, 

    methods: {

    }

</script>

<template> 
    // HTML code - markup
    <div>
        <h1>Hello World</h1>  
    </div>
</template>

<style scoped>
    // CSS code - styles 
    // scoped means limited to the component
</style>

```

2 ways of building a component

1. Options API : old method 
2. Composition API : new method


We gonna start with the options API and then move to the composition API ..

### Vue Templates : 

`templates` written in html + vue + pythonic way = vue templates


* Conditionals In templates : 

`v-if , v-else-if , v-else`

```python
# In python we have  :

if age > 18:
    print("Adult")
elif age < 18:
    print("Not adult")
else:
    print("Age is not specified")
```


In Vue we do

```js
<script> 

<p v-if="age > 18">Adult</p>
<p v-else-if="age < 18">Not adult</p>
<p v-else>Age is not specified</p>

</script> 
```

* For loops :

`v-for`

```python 
for friend in friends:
    print(friend)
```

In Vue: 

```html

The key should be unique 

<template>
  <p v-for="friend in friends" :key="friend"> 
      {{ friend }}
  </p>
</template>
```

```html 

<!-- v-for also has index property and we can do it like  -->

<template> 
    <p v-for="(friend, index) in friends" :key="index"> 
        <span>
            {{ friend }}    
        </span>
        <button v-on:click="removeFriend(index)">x</button>
    </p>
</template>

```


Adding form:: 

`v-model` : acts as a default and binds to the value of input field here     

```html 

<form v-if="present" v-on:submit.prevent="formSubmit">
    <label for="name">Enter Friend Name</label>
    <input type="text" id="fname" name="name" v-model="fname">
    <button v-on:click="addFriend">Add Friend</button>
</form>


```


### Options API : 
CODE IS IN : `App2.vue`

Need to have data() to define the data and for calling methods / attaching a method to a tag alongside exporting and then returning the values from it  


```js

<script>
 export default {
    data(){
        return{
            name: "John Due",
            present: false, 
            age: 20,
            friends: ["John", "Mary", "Tom"]
        }
    }, 
    
    methods :{
      toggleStatus(){
        if(this.present){
          this.present = false
        }
        else if(!this.present){
          this.present = true
        }
      }
    }
 }
</script>
```





### Composition API : 
CODE IS IN : `App.vue`

The `template` remains the same, only the part inside the `script` tag is different and we make it cleaner 


Using `ref` to make it them reactive

Instead of data() and methods, here we use setup()


```js

<script>
  import { ref } from 'vue'

 export default {
  setup(){
    const name = ref("John Due")
    const present = ref(false)
    const age = ref(20)
    const friends = ref(["John", "Mary", "Tom"])
    
    const toggleStatus = () => {
      if(present.value){
        present.value = false
      }
      else if(!present.value){
        present.value = true
      }
    }

    return {
      name,
      present,
      age,
      friends,  
      toggleStatus
    }
  }
 }
</script>

```

A better way : 

Rather than defining the function setup() inside the script body, we can define it alongside script tag, this also removes the need to export and return things as that is added in `setup` added in the script tag

No indentation required for this 

```js

<script setup>
import { ref } from 'vue'
const name = ref("John Due")
const present = ref(false)
const age = ref(20)
const friends = ref(["John", "Mary", "Tom"])

const toggleStatus = () => {
  if(present.value){
    present.value = false
  }
  else if(!present.value){
    present.value = true
  }
}
</script>

```



TO CONTINUE AT : https://youtu.be/VeNfHj6MhgA?feature=shared&t=2900 
