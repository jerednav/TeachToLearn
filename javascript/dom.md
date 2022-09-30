# Document Object Model
- The DOM (or Document Object Model) is a tree-like representation of the contents of a webpage - a tree of “nodes” with different relationships depending on how they’re arranged in the HTML document.
- DOM is a JavaScript representation of a webpage.
- It's objects that you can interact with via JS

```
<div id="container">
  <div class="display"></div>
  <div class="controls"></div>
</div>
```
- The "container" id is a parent of the "display" and "controls" classes.

### But what is the document?
- The document object is our entry point into the world of the DOM. It contains representations of all the content on a page, plus tons of useful methods and properties.
- You can type"console.dir(document)" into the browser console to look at all the methods there are for DOM.

### How do you select DOM elements?
1. Selecting an element
- You select an element from the DOM using selectors or relational properties.
 - ```<div class="display"></div>:``` 
 - You can use display class to manipulate the DOM
   - div.display
   - .display
   - #container > .display
   - div#container > div.d##play
- Once you choose the selector you want to manipulate, you then pick a DOM method to perform that action on the selector.
- When a HTML code is parsed by the web browser, it's converted to the DOM. The primary difference is that these nodes are objects that has it's own set of properties and methods. These methods and properties are what we are going to use to manipulate the DOM.
-
#### DOM methods

**.querySelector**

- selects a single element
```
document.querySelector('h1')
```

**.querySelectorAll**

- select all elements with the selector
- returns a nodelist containing references to all of the matches of the selectors
- 

```
document.querySelectorAll('h1')
```
**innerText**

- represents the "rendered" text content from the node/element, which will include styles

**innerHTML**

- renders the HTML inside div

**textContent**
- renders just the text, good when you need to alter text

#### Element Creation
```
document.createElement(tagName,[option])
```
- creates a new element of tag type tagName. [options] in this case means you can add some optional parameters to the function. Don't worry about these at this point.

```
const div = document.createElement('div')
```

- This function does NOT put your new element into the DOM, it just creates it in memory. This allows you to manipulate the element before putting it on the page.

#### Append Elements
- parentNode.appendChild(childNode) appends childNode as the last child of parentNode
- parentNode.insertBefore(newNode, referenceNode) inserts newNode into parentNode before referenceNode

#### Editing Attributes
 ```
 div.setAttribute('id', 'theDiv');
 //if id exists, update it to 'theDiv", else create an id with value "theDiv"
 
 div.getAttribute('id');
 //returns the value of specified attribute in this case, "theDiv"
 
 div.removeAttribute('id');
 //removes specified attribute
 ```

#### Working with classes
```
div.classList.add('new');                                      
// adds class "new" to your new div

div.classList.remove('new');                                   
// removes "new" class from div

div.classList.toggle('active');                                
// if div doesn't have class "active" then add it, or if
// it does, then remove it
```
It is standard (and cleaner) to toggle a CSS style rather than adding and removing inline CSS.

## Events
- Events are actions that you can manipulate the DOM dynamically.
- Actions such as mouse clicks or keypresses.

There are 3 primary ways to add events.
1. Attach functions' attributes directly on your HTML elements 
2. Set the "on_event" property on the DOM object in your JavaScript
3. Attach event listeners to the nodes in your JavaScript

#### 3 ways to add events
1. Attach functions' attributes directly on your HTML elements 
```
<button onclick="alert('Hello World')">Click Me</button>
```
- Not the best solution because it's cluttering the HTML with the JavaScript

2. Set the "on_event" property on the DOM object in your JavaScript
```
<!-- the HTML file -->
<button id="btn">Click Me</button>
```
```
// the JavaScript file
const btn = document.querySelector('#btn');
btn.onclick = () => alert("Hello World");
```
- This is a little better. We’ve moved the JS out of the HTML and into a JS file, but we still have the problem that a DOM element can only have 1 “onclick” property.

3. Attach event listeners to the nodes in your JavaScript
```
<!-- the HTML file -->
<button id="btn">Click Me Too</button>
```
```
// the JavaScript file
const btn = document.querySelector('#btn');
btn.addEventListener('click', () => {
  alert("Hello World");
});
```
Now, we maintain separation of concerns, and we also allow multiple event listeners if the need arises. Method 3 is much more flexible and powerful, though it is a bit more complex to set up.


