# Portal
- [Portal](#portal)
- [Introduction](#introduction)
- [Installation](#installation)
- [Demo](#demo)
- [Basic operations](#basic-operations)
- [Appendix: Web API study note](#appendix-web-api-study-note)
  - [Introduction](#introduction-1)
    - [Prerequisites](#prerequisites)
  - [Mental model](#mental-model)
  - [Document](#document)
    - [Document Element](#document-element)
      - [Methods](#methods)
        - [```document.documentElement.clientHeight```](#documentdocumentelementclientheight)
        - [```document.documentElement.scrollHeight```](#documentdocumentelementscrollheight)
      - [List of operations](#list-of-operations)
    - [Document Tree](#document-tree)
      - [Shadow DOM](#shadow-dom)
      - [Shadow Tree](#shadow-tree)
    - [TreeWalker](#treewalker)
      - [Methods](#methods-1)
        - [Init](#init)
          - [```Document.createTreeWalker```](#documentcreatetreewalker)
          - [```TreeWalker.filter```](#treewalkerfilter)
          - [```TreeWalker.whatToShow```](#treewalkerwhattoshow)
        - [Navigation](#navigation)
          - [```TreeWalker.currentNode```](#treewalkercurrentnode)
          - [```TreeWalker.firstChild()```](#treewalkerfirstchild)
          - [```TreeWalker.lastChild()```](#treewalkerlastchild)
          - [```TreeWalker.nextNode()```](#treewalkernextnode)
          - [```TreeWalker.nextSibling()```](#treewalkernextsibling)
          - [```TreeWalker.parentNode()```](#treewalkerparentnode)
          - [```TreeWalker.previousNode()```](#treewalkerpreviousnode)
          - [```TreeWalker.previousSibling()```](#treewalkerprevioussibling)
      - [List of operations](#list-of-operations-1)
        - [Create a treewalker](#create-a-treewalker)
      - [Selection](#selection)
        - [Select elements of the same class](#select-elements-of-the-same-class)
          - [Select all the 'a' tags in the body](#select-all-the-a-tags-in-the-body)
        - [CRUD](#crud)
    - [Events](#events)
      - [List of events](#list-of-events)
        - [Mouse](#mouse)
        - [Keyboard](#keyboard)
      - [`GlobalEventHandlers`](#globaleventhandlers)
      - [Keyboard event](#keyboard-event)
        - [Hotkey](#hotkey)
          - [```eventListener + keyup + code + switch case```](#eventlistener--keyup--code--switch-case)
      - [MouseEvent](#mouseevent)
        - [```MouseEvent.clientX```](#mouseeventclientx)
    - [Page properties](#page-properties)
    - [```Node```-related methods](#node-related-methods)
      - [```document.querySelector()```](#documentqueryselector)
      - [```document.querySelectorAll()```](#documentqueryselectorall)
      - [```document.getElementsByClassName()```](#documentgetelementsbyclassname)
      - [```document.getElementById()```](#documentgetelementbyid)
      - [```document.createElement()```](#documentcreateelement)
    - [Tree](#tree)
      - [```document.body```](#documentbody)
    - [With other APIs](#with-other-apis)
      - [```document.createTreeWalker()```](#documentcreatetreewalker-1)
      - [```document.createNodeIterator()```](#documentcreatenodeiterator)
  - [Node](#node)
    - [Document type node](#document-type-node)
    - [Non-document type node](#non-document-type-node)
    - [Mental model](#mental-model-1)
    - [Modification(CRUD)](#modificationcrud)
      - [Logic](#logic)
        - [```Node.compareDocumentPosition(otherNode)``` - >Relations](#nodecomparedocumentpositionothernode---relations)
        - [```Node.hasChildNodes()``` - >EndDetection](#nodehaschildnodes---enddetection)
        - [```Node.isSameNode(otherNode)``` - > Same?](#nodeissamenodeothernode----same)
      - [Addition](#addition)
        - [```element.appendChild(aChild)``` - Append()](#elementappendchildachild---append)
        - [```Node.insertBefore(newNode, refNode)``` - insertBefore()](#nodeinsertbeforenewnode-refnode---insertbefore)
      - [Remove](#remove)
        - [```Node.removeChild(child)``` - Remove()](#noderemovechildchild---remove)
      - [Move](#move)
      - [Update](#update)
        - [```Node.replaceChild(newCh, oldCh)``` - replace(n, o)](#nodereplacechildnewch-oldch---replacen-o)
      - [Clone](#clone)
        - [```Node.cloneNode([deep])``` - deepClone()](#nodeclonenodedeep---deepclone)
    - [Selection](#selection-1)
      - [```Node.ChildNode```](#nodechildnode)
      - [```Node.ParentNode```](#nodeparentnode)
      - [NodeFilter](#nodefilter)
        - [```Node.filter.acceptNode()```](#nodefilteracceptnode)
      - [NodeIterator](#nodeiterator)
      - [```NonDocumentTypeChildNode.nextElementSibling``` - >SelectNext](#nondocumenttypechildnodenextelementsibling---selectnext)
      - [```NonDocumentTypeChildNode.previousElementSibling``` - >SelectPrev](#nondocumenttypechildnodepreviouselementsibling---selectprev)
        - [Usage](#usage)
    - [Query](#query)
      - [NodeList](#nodelist)
        - [Usage](#usage-1)
  - [Window](#window)
    - [Properties](#properties)
      - [```window.scrollX```](#windowscrollx)
      - [```window.scrollY```](#windowscrolly)
    - [Difference between ```window``` and ```document```](#difference-between-window-and-document)
  - [DOMTimeStamp](#domtimestamp)
  - [Element](#element)
    - [Contents](#contents)
      - [```Element.innerHTML```](#elementinnerhtml)
      - [```Element.outerHTML```](#elementouterhtml)
      - [```Element.innerText```](#elementinnertext)
      - [```Element.outerText```](#elementoutertext)
    - [Style](#style)
      - [Basics](#basics)
      - [```Element.scrollHeight```](#elementscrollheight)
    - [Node navigation](#node-navigation)
      - [```Element.closest()```](#elementclosest)
      - [```Element.classList```](#elementclasslist)
        - [```Element.classList.toggle([className])```](#elementclasslisttoggleclassname)
  - [Event](#event)
    - [What is event?](#what-is-event)
    - [Event capturing and bubbling](#event-capturing-and-bubbling)
      - [Target phase](#target-phase)
      - [Event phase](#event-phase)
      - [Bubble phase](#bubble-phase)
    - [Attributes](#attributes)
      - [Target](#target)
        - [closest](#closest)
    - [Event Listener](#event-listener)
      - [Syntax](#syntax)
    - [Event Loop](#event-loop)
      - [Resource](#resource)
    - [Event Target](#event-target)
    - [Troubleshoot](#troubleshoot)
      - [```Uncaught TypeError: Cannot read property 'addEventListener' of null```](#uncaught-typeerror-cannot-read-property-addeventlistener-of-null)
      - [```Uncaught TypeError: Cannot create property '[genericEvent]' on [Element]```](#uncaught-typeerror-cannot-create-property-genericevent-on-element)
  - [Operations](#operations)
    - [Navigation](#navigation-1)
      - [Node tree](#node-tree)
    - [Selection](#selection-2)
      - [Get multiple elements](#get-multiple-elements)
        - [```Array.from```](#arrayfrom)
  - [Resource](#resource-1)
# Introduction
- This is the first web application I developed. It was crude, it was awful. The JavaScript is sort of a confusing mixture of ES6 and arcade JavaScript. None of those reusable components or other good stuff here. The CSS code was all over the place, with no media queries or any cross-browser support like `-webkit-`. But at that time, in front of hundreds of people, it worked. Except I suffered from serious intercostal neuralgia for a few days. 
- I deleted all of the images and sensible data
- I kept all of my *shitty* design process in `./structure.pdf`

# Installation
1. Install Vscode
2. git clone \[thisProject\]
   - [This is not a porn site](./img/cat.jpg)
3. Open with Vscode
   - [Help, I don't know what vscode is](./img/cat.jpg)
4. Install `Live Preview` extension
   - [I pretend this is a tutorial link](./img/cat.jpg)
5. Preview

# Demo
[Uncaught SyntaxError: Pretending to be a demo](https://portfolio-ost.herokuapp.com/#/portfolio)

# Basic operations
   Keyboard shortcuts:  
      1 ---  Fourth prize  
      2 ---  Third prize  
      3 ---  Second prize  
      4 ---  First prize  
      5 ---  Special prize  
      6 ---  Lucky Boss  
      7 ---  Lucky Star  
      8 ---  Lucky actor  
      SPACE  ---  Start/Stop  
      R ---  RESET  
      ENTER --- Toggle fullscreen(browser)  
      T ---  Destroy toggleJumpscare  
      BACKSPACE --- Delete last chosen candidate(Undo)  
    

# Appendix: Web API study note
- For this project, the most stuff I've learned is Web API, here's the Web API note I've gathered

## Introduction
### Prerequisites
- JavaScript - Array
## Mental model
## Document
Tip:
- Consider merging the *Document* section and the *Node* section for their operations kind of intertwine one another.

### Document Element
#### Methods
##### ```document.documentElement.clientHeight```
- Examples
  - [vue](https://codepen.io/zhutoutoutousan/pen/MWymOXV)

##### ```document.documentElement.scrollHeight```
- Examples
  - [vue](https://codepen.io/zhutoutoutousan/pen/MWymOXV)

#### List of operations
### Document Tree
#### Shadow DOM
[MDN - Using Shadow DOM](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_shadow_DOM)
#### Shadow Tree
### TreeWalker
#### Methods
##### Init
###### ```Document.createTreeWalker```
###### ```TreeWalker.filter```
###### ```TreeWalker.whatToShow```
##### Navigation
###### ```TreeWalker.currentNode```
###### ```TreeWalker.firstChild()```
###### ```TreeWalker.lastChild()```
###### ```TreeWalker.nextNode()```
###### ```TreeWalker.nextSibling()```
###### ```TreeWalker.parentNode()```
###### ```TreeWalker.previousNode()```
###### ```TreeWalker.previousSibling()```
#### List of operations
##### Create a treewalker
```javascript

/*
document.createTreeWalker(root, whatToShow[, filter[, entityReferenceExpansion]])
- root: A root Node of this TreeWalker traversal, e.g. document.body
- whatToShow: 
  - unsigned long
  - RTFM for more
  - https://developer.mozilla.org/en-US/docs/Web/API/Document/createTreeWalker
- filter --> NodeFilter
- entityReferenceExpansion --> Obsolete, just set to false
Explore it in the chrome console.

After initialization, further operations can be done with the Node API.
*/
let treeWalker = document.createTreeWalker(
  document.body,
  NodeFilter.SHOW_ELEMENT,
  { acceptNode: function(node) { return NodeFilter.FILTER_ACCEPT; } },
  false
)

// Push all of the page elements into an array
let nodeList = [];
let currentNode = treeWalker.currentNode;

while(currentNode) {
  nodeList.push(currentNode);
  currentNode = treeWalker.nextNode();
}
```
#### Selection
##### Select elements of the same class
```javascript
// Other codes the same 
const classNameYouWant = "classNameYouWant";
while(currentNode) {
  if(currentNode.class === classNameYouWant) {
    nodeList.push(currentNode);
  }
  currentNode = treeWalker.nextNode();
}
```

###### Select all the 'a' tags in the body
##### CRUD


### Events
#### List of events
##### Mouse
##### Keyboard
- keyup
- keydown
#### `GlobalEventHandlers`
- onBlur
  - [What is the difference between onBlur and onChange attribute in HTML?](https://stackoverflow.com/questions/785099/what-is-the-difference-between-onblur-and-onchange-attribute-in-html)
- onChange
#### Keyboard event
##### Hotkey
###### ```eventListener + keyup + code + switch case```
Comments:
- ```keyCode``` is deprecated, try to use ```code```
  - [KeyboardEvent.code - MDN](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/code)
```javascript

const triggerEvent_1 = (in) => {
  // DO
}

const triggerEvent_2 = (in) => {
  // DO
}

const triggerEvent_3 = (in) => {
  // DO
}

// ...

const assignHotkey = function() {
    document.addEventListener("keyup", function(event) {
      switch(event.code) {
        case '1':
          triggerEvent_1();
        break;
        case '2':
          triggerEvent_2();
        break;
        case '3':
          triggerEvent_3();
        break;
        // ...
      }
    })
}
```
#### MouseEvent
##### ```MouseEvent.clientX```
### Page properties
### ```Node```-related methods
#### ```document.querySelector()```
#### ```document.querySelectorAll()```
#### ```document.getElementsByClassName()```
#### ```document.getElementById()```
#### ```document.createElement()```
### Tree
#### ```document.body```
```javascript
const div = document.createElement('div');
div.className = 'foo';
```
### With other APIs
#### ```document.createTreeWalker()```
#### ```document.createNodeIterator()```
## Node
### Document type node 
### Non-document type node
### Mental model
Exercise
- Implementation proficiency: Think of as many operations as you can concerning DOM tree operations and consider how to implement them into actual code.
- Visual aids: Try to visualize the exercise process mentioned above
### Modification(CRUD)
#### Logic
##### ```Node.compareDocumentPosition(otherNode)``` - >Relations
##### ```Node.hasChildNodes()``` - >EndDetection
##### ```Node.isSameNode(otherNode)``` - > Same?
#### Addition
##### ```element.appendChild(aChild)``` - Append()
##### ```Node.insertBefore(newNode, refNode)``` - insertBefore() 
#### Remove
##### ```Node.removeChild(child)``` - Remove()
#### Move
#### Update
##### ```Node.replaceChild(newCh, oldCh)``` - replace(n, o)
#### Clone
##### ```Node.cloneNode([deep])``` - deepClone()

### Selection
#### ```Node.ChildNode```
#### ```Node.ParentNode```
#### NodeFilter
##### ```Node.filter.acceptNode()```
#### NodeIterator
#### ```NonDocumentTypeChildNode.nextElementSibling``` - >SelectNext
#### ```NonDocumentTypeChildNode.previousElementSibling``` - >SelectPrev
##### Usage
- carousel slide
- accordian
### Query
#### NodeList
##### Usage
- carousel slide
- accordian


## Window
### Properties
#### ```window.scrollX```
- Examples
  - [vue](https://codepen.io/zhutoutoutousan/pen/MWymOXV)
#### ```window.scrollY```
- Examples
  - [vue](https://codepen.io/zhutoutoutousan/pen/MWymOXV)

### Difference between ```window``` and ```document```

## DOMTimeStamp
## Element
### Contents
#### ```Element.innerHTML```
#### ```Element.outerHTML```
#### ```Element.innerText```
#### ```Element.outerText```
### Style
#### Basics
- Naming tradition: CSS(pascal case) --> JavaScript(Camel case)
#### ```Element.scrollHeight```
### Node navigation
#### ```Element.closest()``` 
#### ```Element.classList```
##### ```Element.classList.toggle([className])```

For more see [Element.classList - MDN](https://developer.mozilla.org/en-US/docs/Web/API/Element/classList)
## Event
### What is event?
```javascript
const someEvent = event => {
  console.log(event)
}
```
### Event capturing and bubbling
#### Target phase
#### Event phase
#### Bubble phase
### Attributes
#### Target
##### closest
See ```Element.cloest()```
### Event Listener
#### Syntax
```javascript
const someEvent = event => {
  // some operations
  return;
}

let someElement = document.querySelector('.someClass');
someElement.addEventListener(someEvent);
```
### Event Loop
#### Resource 
[What is Event loop? - Jsconf](https://www.youtube.com/watch?v=8aGhZQkoFbQ)
### Event Target
### Troubleshoot
#### ```Uncaught TypeError: Cannot read property 'addEventListener' of null```
- Check if the script file is included before the page is loaded.
  - [Stack overflow](https://stackoverflow.com/questions/57191982/how-to-fix-typeerror-cannot-read-property-addeventlistener-of-null)

#### ```Uncaught TypeError: Cannot create property '[genericEvent]' on [Element]```
- Maybe you used ```for(const i in SomeNodeList)``` when batch assigning events to class elements. Generally ```SomeNodeList``` has an additional ```length``` attribute. Try traverse with respect to its ```SomeNodeList.length```.

## Operations
### Navigation
#### Node tree
### Selection
#### Get multiple elements
##### ```Array.from```

## Resource
[DOM - MDN](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model)