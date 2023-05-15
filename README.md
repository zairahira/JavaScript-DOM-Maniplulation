# JavaScript-DOM-Maniplulation

# DOM Manipulation

## What is DOM

DOM stands for Document Object Model. It is a programming interface for web documents that allows scripts to dynamically access and modify the content, structure, and style of a document.

When a web page is loaded into a web browser, the browser creates a Document Object Model of the page, which is essentially a tree-like representation of the HTML structure of the page. Each element in the page, such as a paragraph or a button, is represented as an object in the tree, and these objects can be accessed and manipulated using programming languages such as JavaScript.

By manipulating the DOM, web developers can create dynamic and interactive web pages that respond to user input, update content dynamically, and more. Common use cases of manipulating the DOM include updating the text or style of an element in response to a user action, adding or removing elements from the page, and animating elements on the page.

## Example of DOM:

In this diagram, the root of the tree is the HTML element. It has three children: head, body, and footer. The head and body elements each have their own children, and so on. Each element is represented as a box, and the lines between the boxes represent parent-child relationships. The text inside each box represents the tag name of the element. Note that this is a simplified diagram and the actual structure of a web page's DOM tree can be much more complex.

```
          ┌───────── HTML ─────────┐
          |                         |
     ┌────┴────┐             ┌────┴────┐
<head>        <body>       <footer>  ...
 |             |             |
 |        ┌────┴────┐    ┌───┴───┐
 |      <title>   ...   <nav>  ...
 |        |                |
 |        └────────┐  ┌────┴────┐
 |                  \/<a>      <a>
 |               text  |      text
 |                     |
 └─────────────────────┘


```



## 5 ways to select elements in a DOM

###   `getElementById()`

Selects the element by the id, startis with # in html tag

```javascript
const  title = document.getElementById('main-heading');
console.log(title);
```

###   `getElementByClassName`

```javascript
const  listItem = document.getElementsByClassName('list-items');
console.log(listItem);
```

###   `getElementsByTagName()`

```javascript
const  listItem = document.getElementsByTagName('li');
console.log(listItem);
```

###   `queryselector()`

```javascript
// selects only the first occurrence  
const  container = document.querySelector('div');
console.log(container);
```

###   `querySelectorAll()`

```javascript
// selects all of the occurrences

const  container = document.querySelectorAll('div');
console.log(container);
```

## Styling an element

```javascript
const  title = document.querySelector('#main-heading');
title.style.color = 'red';
```

### Styling multiple elements, like list items

Loop is required to apply a style to multiple items.

const  listItems = document.querySelectorAll('.list-items'); //classes start with a dot

```javascript
//listItems.style.color = 'red';
for(i = 0; i <listItems.length; i++){

  listItems[i].style.color = 'red';
    listItems[i].style.fontSize = '5rem'; 
}
```

## Creating new elements using `document.createElement()`

  
```javascript
const  ul = document.querySelector('ul');
const  li = document.createElement('li');

// Adding elements
ul.append(li);
  
// check in console and elements tab, there would be an emplty `<li>`

console.log();
```

## Modifying text using `innerText`, `textContent` and `innerHTML`

```javascript
const  firstListItem = document.querySelector('.list-items');    
console.log(firstListItem.innerText);
console.log(firstListItem.textContent);    
console.log(firstListItem.innerHTML); // not recommended due to security issues
```

## Modifying element attributes and classes using `setAttribute()` and `removeAttribute()`

```javascript
//Modifying the text
li.innerText = "X-men";


// Modifying attributes and classes 
li.setAttribute('class', 'list-items');

// remove attribute
li.removeAttribute('class')
```

## Modifying element attributes and classes using `classList.add()` and `classList.remove()`

```javascript
li.classList.add('list-items'); // same as li.setAttribute('class', 'list-items');
li.classList.remove('list-items')
```
  

## Find if an element has a specific class using `classList.contains()`

```javascript
console.log(li.classList.contains('list-items'));
```

# Traversing the DOM

## Parent node traversal

```javascript
let  ul = document.querySelector('ul');

console.log(ul.parentNode);
console.log(ul.parentElement);

// parent's parent
console.log(ul.parentNode.parentNode); // parent's parent
console.log(ul.parentElement.parentNode); // parent's parent 
```

## Minute difference between `.parentNode` and `.parentElement`

```javascript
const  html = document.documentElement;

console.log(html.parentElement); // returns null
console.log(html.parentNode); // returns #document
```
    
   
## Child node traversal

```javascript
let  ul = document.querySelector('ul');
    
console.log(ul.childNodes);
console.log(ul.firstChild);
console.log(ul.lastChild);

    
ul.childNodes[1].style.backgroundColor = 'blue';
```

## Sibling traversal

```javascript
let  ul = document.querySelector('ul');   

console.log(ul.previousElementSibling);    
console.log(ul.nextElementSibling);    
console.log(ul.nextSibling);    
console.log(ul.previousSibling);
```

## Event listeners
See the sample file: eventlistener.html.

1. Include directly in HTML

```html
<button  onclick="alert('I love JS')">Enter</button>
```

2. Click event

```javascript
const buttonTwo = document.querySelector('.btn-2')

function alertBtn() {
    alert('i love js2');
};

buttonTwo.addEventListener("click", alertBtn);


```

3. mouseover event

```html
<div id="my-element">Hover over me</div>

```

```js
const element = document.getElementById("my-element");

element.addEventListener("mouseover", function() {
  console.log("Mouse is over the element");
});

```

More event listeners: https://www.w3schools.com/jsref/dom_obj_event.asp



## Event propagation

There are three phases of event propagation:

1.  Capturing phase: During this phase, the event is first captured by the outermost element (the root of the DOM tree) and then propagated down through the nested elements until it reaches the target element.
    
2.  Target phase: During this phase, the event has reached the target element, and any event listeners attached to the target element will be executed.
    
3.  Bubbling phase: During this phase, the event is propagated back up the DOM tree from the target element to the outermost element, and any event listeners attached to any of the elements in the path will be executed.

**sample HTML:**

```html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <div class="div2">
    2
    <div class="div1">
      1
      <button>click</button>
    </div>
  </div>
</body>
<script src="app.js"></script>

</html>
```


## event capturing

```javascript

// Event propagation

// bubbling off by default

window.addEventListener("click", function () {
    console.log('window')
}, true);


document.addEventListener("click", function () {
    console.log('Document')
}, true);


document.querySelector(".div2").addEventListener
    ("click", function () {
        console.log('DIV 2')
    }, true);

document.querySelector(".div1").addEventListener
    ("click", function () {
        console.log('DIV 1')
    }, true);


document.querySelector("button").addEventListener
    ("click", function (e) {
        console.log(e)
        // `e`is event object, has details of the target element.
    }, true);
```


to initiate bubbling, set `true` to `false`.
also, false by default

```javascript


// Event propagation

// bubbling on

window.addEventListener("click", function () {
    console.log('window')
}, false);


document.addEventListener("click", function () {
    console.log('Document')
}, false);


document.querySelector(".div2").addEventListener
    ("click", function () {
        console.log('DIV 2')
    }, false);

document.querySelector(".div1").addEventListener
    ("click", function () {
        console.log('DIV 1')
    }, false);


document.querySelector("button").addEventListener
    ("click", function (e) {
        console.log(e)
    }, false);

```


you can stop bubbling with `stopPropagation()`

## stop event bubbling and capturing with `stopPropagation()`

you can also stop event capturing with `stopPropagation()

### stop bubbling

```javascript
// Stop Event bubbling

window.addEventListener("click", function () {
    console.log('window')
}, false);


document.addEventListener("click", function () {
    console.log('Document')
}, false);


document.querySelector(".div2").addEventListener
    ("click", function (e) {
        e.stopPropagation();
        console.log('DIV 2')
    }, false);

document.querySelector(".div1").addEventListener
    ("click", function () {
        console.log('DIV 1')
    }, false);


document.querySelector("button").addEventListener
    ("click", function (e) {
        console.log(e)
    }, false);

```

### stop capturing

set `false` to `true`

```javascript
// Event propagation

// bubbling off by default

window.addEventListener("click", function () {
    console.log('window')
}, true);


document.addEventListener("click", function () {
    console.log('Document')
}, true);


document.querySelector(".div2").addEventListener
    ("click", function (e) {
        e.stopPropagation();
        console.log('DIV 2')
    }, true);

document.querySelector(".div1").addEventListener
    ("click", function () {
        console.log('DIV 1')
    }, true);


document.querySelector("button").addEventListener
    ("click", function (e) {
        console.log(e)
    }, true);

```




`once: true` fire off once.

```javascript
// DIV 2 would be fired only once
document.querySelector(".div2").addEventListener
    ("click", function (e) {
        // e.stopPropagation();
        console.log('DIV 2')
    }, { once: true });

```


In that case, the `true` is a boolean value used to indicate whether the event should be handled in the capturing phase or the bubbling phase of the event propagation. If `true` is used, the event is handled in the capturing phase, and if `false` is used (or omitted), the event is handled in the bubbling phase.

## Event delegation

### Attaching a style to parent to apply to children

```html

// Event propagation
// Event delegation
// append a single event listener to a parent element that adds it to
//all of its present and future descendants that match a selector

<!DOCTYPE  html>
    <html lang="en">
        <head>
            <meta charset="utf-8" />
            <title>Events: Task 3</title>
        </head>
        <body>
            <ul id="sports">
                <li>Football</li>
                <li>Basketball</li>
                <li>Baseball</li>
            </ul>

            <script>
                document.querySelector('#sports').addEventListener
                ('click', function(e){
                    console.log(e.target.getAttribute('id') + 'is clicked');
                const  target = e.target;
                if(target.matches('li')){
                    target.style.backgroundColor = 'lightgrey';
}
})
            </script>
        </body>
    </html>

```
