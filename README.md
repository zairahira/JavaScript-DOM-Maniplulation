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
selects the element by the id, startis with # in html tag

    const  title = document.getElementById('main-heading');
    console.log(title);


###   `getElementByClassName`

    const  listItem = document.getElementsByClassName('list-items');
    console.log(listItem);

###   `getElementsByTagName()`

    const  listItem = document.getElementsByTagName('li');
    console.log(listItem);

###   `queryselector()`

    // selects only the first occurrence  
    
    const  container = document.querySelector('div');
    console.log(container);

###   `querySelectorAll()`

    // selects all of the occurrences
    
    const  container = document.querySelectorAll('div');
    console.log(container);

## Styling an element

  

    const  title = document.querySelector('#main-heading');
    
    title.style.color = 'red';

### Styling multiple elements, like list items

Loop is required to apply a style to multiple items.

    const  listItems = document.querySelectorAll('.list-items'); //classes start with a dot
    
    //listItems.style.color = 'red';
    
      
    
    for(i = 0; i <listItems.length; i++){
    
	    listItems[i].style.color = 'red';
        listItems[i].style.fontSize = '5rem'; 
     
    }


## Creating new elements using `document.createElement()`

  

    const  ul = document.querySelector('ul');
    const  li = document.createElement('li');
    
    // Adding elements
    ul.append(li);
      
    // check in console and elements tab, there would be an emplty `<li>`
    
    console.log();


## Modifying text using `innerText`, `textContent` and `innerHTML`

    const  firstListItem = document.querySelector('.list-items');
    
     
    console.log(firstListItem.innerText);
    console.log(firstListItem.textContent);    
    console.log(firstListItem.innerHTML); // not recommended due to security issues


## Modifying element attributes and classes using `setAttribute()` and `removeAttribute()`

 
  

    //Modifying the text
    
    li.innerText = "X-men";
    
      
    // Modifying attributes and classes 
    
    li.setAttribute('class', 'list-items');
    
      // remove attribute
    
    li.removeAttribute('class')

## Modifying element attributes and classes using `classList.add()` and `classList.remove()`

    li.classList.add('list-items'); // same as li.setAttribute('class', 'list-items');
    li.classList.remove('list-items')

  

## Find if an element has a specific class using `classList.contains()`

    console.log(li.classList.contains('list-items'));

# Traversing the DOM

## Parent node traversal

    let  ul = document.querySelector('ul');
    
    console.log(ul.parentNode);
    console.log(ul.parentElement);

 
 

    // parent's parent
    console.log(ul.parentNode.parentNode); // parent's parent

    
    console.log(ul.parentElement.parentNode); // parent's parent 
  
## Minute difference between `.parentNode` and `.parentElement`


    const  html = document.documentElement;
    
      
    
    console.log(html.parentElement); // returns null
    
    console.log(html.parentNode); // returns #document
