---
layout: post
title: Learning Playwright and web 
date: 2025-01-12
---

[Playwright](https://playwright.dev/python/)

# Web

The current web page is advanced , the DOM is loaded only for the visible section on the page and the visible section can be increased or decreased based on the viewport height and width of the page .. 

To load the DOM in natural way you will need to scroll it down to get to the next set of links and it builds the DOM tree and the tree !!


## google
In google, the top level links are in <h3>  


## End to end automation using playwright 

test files start with `test_` like : `test_example.py`  

Go to link :  page.goto('https://playwright.dev')

Extract title : expect(page).to_have_title(re.compile("Playwright"))

Find a link with the name and click it  = page.get_by_role("link" , name="Get Started").click()

Expect page to have a heading with the name of Installation : 

Almost everything starts with going to a page: 

Goto : page.goto(url)

Interactions 
For interactions, we need to locate the elements. 
Playwright auto waits for elements to be actionable prior to performing the action. 

locater_made = page.get_by_role("link", name="Get Started") # hover
locater_made.click()

Radio element check : create a locator using page.get_by_role("checkbox").check()
Hover element : locator.hover()  
Fill : locator.fill("Name") , here locator should be able to take some input 
Press Key : locator.press("<keyname>") , can be : "Backspace" , "ArrowLeft" , .. etc 
Select Option : locator.select_option("<select_option>")


Assertions: 
expect(locator).to_be_checked(), checkbox is checked 

```python 

## Before assertion : 
<input type="checkbox" id="newsletter" />
<label for="newsletter">Subscribe to newsletter</label>


## After assertion :
<input type="checkbox" id="newsletter" checked />
<label for="newsletter">Subscribe to newsletter</label>

```


Actions
Interaction with HTML input elements using  `fill()` 
# Text input
await page.get_by_role("textbox").fill("Peter") => locator.fill("<fill-value>")

Typing the characters sequentially in a input field: 
# Press keys one by one
await page.locator('#area').press_sequentially('Hello World!')

Press the keyboard keys : 

```python

await page.get_by_text("Submit").press("Enter") , press the enter button 

await page.get_by_role("textbox").press("Control+ArrowRight")

```

Mouse down and Mouse up 

await page.locator().hover()

await page.mouse.down() : keep the button pressed 

await page.mouse.up() : release the button 

one down() + one up() : means that a single click happened 


Go to the last, forcing "infinite list" to load more content 
await page.get_by_text("Footer text").scroll_into_view_if_needed()


ScreenShot

```python
screenshot an element matching the locator ... 

await page.get_by_role("link").screenshot(animations="disabled", path="link.png")

animation : disable,
path : path_to_store_image 
```

bounding box 

Creates a bounding box of the element matching the locator !

```python
box = await page.get_by_role("button").bounding_box()
await page.mouse.click(box["x"] + box["width"] / 2, box["y"] + box["height"] / 2)
```

Browser: 

Playwright requires specific version of browser binaries to operate , using playwright CLI 
You can use any chromium browser that so a good choice would be to use brave browser .. 










