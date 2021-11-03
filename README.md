## JavaScript 

### JSX
A syntax extension of JavaScript created for the React JavaScript framework.

### Vanilla JavaScript 
or Vanilla JS, is the core language of JavaScript.

### ECMAScript
The broswer specification of the JavaScript language. It is not the language itself, but the official description of how the language should be interpreted by browsers. Using ECMAScript usually means also using Babel.js to make it work in current browser implementations.

### TypeScript (.ts)
Variation, dialect, or flavor of JavaScript introducing features like strong typing. 

### React, Vue, Angular
JavaScript framework allowing us to write JavaScript-based front-end applications. React.js, Vue.js, and Angular.js, they all add an abstruction layer on the top of JavaScript to do things in a more streamlined and efficient way.

### npm, WebPack, Gulp
Build tools and infrastructure to automate the process of optimizing human-readable JavaScript for the best browser performance.

### Node.js
The ubiquitous JavaScript server runtime used to run JavaScript everywhere; used to run npm, WebPack, Babel, and so on. We will be interfacing with Node.js on computer all the time, through the Node package manager or NPM.



## Up and running with JS 
### javaScript in an HTML document
The script tag can be placed anywhere within the HTML document. Technically speaking, you would want to place it in the head section because it's a meta part of the document, and it's npt part of the actual document . But in many cases, script tags are always placed at the very end of the document. Browser read HTML from the top, line by line. It renders it out as it reads it and then anytime it encounters JavaScript everything stops that's because the JavaScript may make changes to the document, and then reads all the JavaScript. renders the JavaScript and thne goes back to the rendering the entire page.

### JavaScript as an external file
<script src="script.js"></script>

### Modern JavaScript loading
async and defer keywords: tightly control how and when JavaScript is loaded, and they need a bit of explanation. 

#### Default behavior: (reference a script and point to the file)
The browser start parsing the HTML document, up until the point where it finds this reference, then it **stop parsing the HTML**, goes **downloads the JS file**, then **executes whatever is in the JS**, then picks up the HTML parsing. It is called content or render blocking.
#### Async keyword:
When meets a JS, **keep parsing the HTML while download the JS**, **only stop parsing when you actually have the file**, then executes whatever's in the JS, then continue HTML parsing. 
#### Defer keyword:
Tells browser that parse HTML and if you encounter JS, just **load JS alongside your HTML parsing**, then **when the HTML parsing is complete, execute whatever JS you have**.
<script src="script.js" **defer**></script>

Loading JS in the footer, is now an anti-pattern. JavaScript should always be loaded in the head, and then use async or defer, to control when that JS is executed on the document.

### JavaScript modules
Allows us to break pieces out of JS file and place them in a seperate file, and then import them back into the original file again. 
    <script type="module" src="backpack.js"></script>
    <script type="module" src="script.js"></script>
    1. we need to import all Js files. They may rely on each other.
    2. when we set type="module" they automatically get deferred. 
    3. the objects in module Js is only available in the context of script itself, we can not call the objects in browser's console. So think carefully what things you should put in module. 
    
    
## Objects
JaveScript is a prototype-based object oriented programming language, which means that when we work with JS, we are working with objects that are based on prototypes(attributes). Each object is a unique instance of an object prototype. 
  {}: curly brackets define data as an object.
  property: name-value pair, separated by a colon.
  method: properties containing functions.
  
#### object container
const: constant. Objects are typyically constants: we can change the properties of the object inside the container. We can't remove or replace the object from the container. 
#### object properties
property name can only contain letters, digits, dollar signs and underscores. 
JavaScript does not allow for hyphens in property names. When targeting CSS properties, use camelCase, so the "font-family" property becomes "fontFamily".
#### accessing object properties
1. dot notation
    console.log("the pockateNum: ", backpack.pocketNum);
2. bracket notation, can be used when there is non-standard property name.
    console.log("the pockateNum: ", backpack["pocketNum"]);
#### object method
functions sitting inside objects.
    1.
    toggleLid: function (lidStatus) {
    this.lidOpen = lidStatus;
  },
or its short version:
    2.
functions sitting inside objects.
    toggleLid(lidStatus) {
    this.lidOpen = lidStatus;
  },
Object methods must be declared using function expressions or the method definition shorthand, and can't use arrow functions. 
#### classes: object blueprints or templates
1. Class declaration: class Name {}
2. Class expression:  const Name = class {}
#### object constructors
The diffrence between the class and the obejct constructor is that the methods live inside the main construction function just like the properties do, whereas in the class, the definition of these methods happens outside the main constructor function, and there is no need semicolon to separate them. Only ues object constructor when you editing a old system which is not support the class, since class is a new term in JS.
#### global objects
In addition to the obejcts that are created by yourseld, the browser has a long list of default objects you can use for a variety of different purposes.

Object's name can't be same with its class name. If the calss is a constant, this will cause an error. If the class is not a constant, the new object will overwrite the class.

## String output
#### Template literals
back ticks tell the browser that anything inside here is a template literal, meaning we can mix HTML and strings.
move this part from the html <body> ... </body>
```
    <main>
      <article>
        <h1>Everyday Backpack</h1>
        <ul>
          <li>Volume:</li>
          <li>Color:</li>
          <li>Age:</li>
          <li>Number of pockets:</li>
          <li>Left strap length:</li>
          <li>Right strap length:</li>
          <li>Lid status:</li>
        </ul>
      </article>
    </main>
```
to JS
```
const content = `
    <main>
      <article>
        <h1>${everydayPack.name}</h1>
        <ul>
          <li>Volume: ${everydayPack.volume}</li>
          <li>Color: ${everydayPack.color}</li>
          <li>Age: ${everydayPack.backpackAge()}</li>
          <li>Number of pockets: ${everydayPack.pocketNum}</li>
          <li>Left strap length: ${everydayPack.strapLength.left}</li>
          <li>Right strap length: ${everydayPack.strapLength.right}</li>
          <li>Lid status: ${everydayPack.lidOpen}</li>
        </ul>
      </article>
    </main>
`;

document.body.innerHTML = content;
```
#### conventional way without template literal
```
const content = "<h1>" + everydayPack.name + "</h1>";
```

## DOM
DOM: document object model. It describe the hierarchical tree structure for a HTML document.
DOM is short for "Document Object Model", the document object the browser creates when it renders an HTML document.
#### Acceess elements with querySelector
Both querySelector and querySelectorAll methods take CSS query as their perameter.
The querySelector returns a DOM object (first match), and it is a pure JavaScript object. This is basically using CSS in JavaScript.  
```
document.querySelectorAll("main span")  // return type: NodeList
```
#### access elements using older methods
```
document.getElementsByClassName("packprop backpack__color")  // parameter has two class names; it returns HTMLCollections
document.getElementById("everyday")
```
#### Modifying element classes
```
// old method
document.querySelector("h1").className = "new-class" // but we should be careful about using the class name property, especially in React and other framework.
// instead, we can use classList property, which gives a Dom token collection of all the classes appended to an elememt.
document.querySelector("main li:first-child").classList.add("new-class")
document.querySelector("main li:first-child").classList.remove("new-class")
document.querySelector("main li:first-child").classList.toggle("new-class") // add if it is not there, remove it exists.
document.querySelector("main li:first-child").classList.replace("packprop","new-class")
document.querySelector("main li:nth-child(3)")    // get the 3rd li child
```
#### Attributes
```
document.querySelector("img").attributes // return a NameNodeMap
document.querySelector("img").hasAttribute("src") // return boolean
document.querySelector("img").getAttribute("src")
document.querySelector("img").setAttribute("alt","a drawing of backpack")
document.querySelector("img").removeAttribute("title")
```
#### Inline style
If an element has inline styles, meaning there are CSS declarations in the element itself. That inline CSS is stored in the style property of the elements.
```
document.querySelector(".site-title").style   // contains every possible property
document.querySelector(".site-title").style.color = "rebeccapurple"   // change color property
```
#### Add DOM elements
```
const newArticle = document.createElement("article");   // create new element
newArticle.classList.add("backpack");   // give it class
newArticle.setAttribute("id", "everyday");   // give it id
newArticle.innerHTML = content;   // set content (template literal)
main.append(newArticle);   // add it to the end of an exist element
// ParentNode.prepend(NewElement) add it to the begining od an exist element
// other methods: appendChild(), replaceChild(), insertBefor(), insertAdjcentElement()
```

## Variables and Data Types
#### var
classic variable container. var is mutable, globally-scoped variable, and we can change its data type. It is the default variable type, we don't need to explicitly use "var" to define a var in console, but in editor we need to do so. 
```
var container = 5, x = 3, y = "blu"
```
var is global-scoped variable, meaning that even we change a var's value inside a function, the new assignment applies everywhere in the document after the instance (where you call the function). 
#### let
block-scoped local variable, safely avoid variable scope issue.
```
function headingColor() {
  let color = "blue";
  document.querySelector(".title").style.color = color;
}
```
If we use the let variable outside the block, there is an error. When browser run it, it encounter the error, and it won't render the rest part of JS after the error. So normally use **let** instead **var**, they both mutable.
#### const
define block-scoped constant. 
We can't put new stuff in the const box. That doesn't mean we can't change the status or properties or other features of what the constant holds.
#### data types
JavaScript is a weekly typed language, meaning you don't have to declare what type of data goes into your variables. 
Include: String, number, boolean, null, undefined, object, array.  
```
// use typeof operator 
typrof variableName
```
#### Assignment vs. Comparison
"=" : assignemnt of a value to a variable.
"==", "!=": loose comparison, or semiotic equivalent,  meaning are the values are same. 
"===", "!==" : absolute equivalence test
```
5 == "5" // returns true, because the values looks same. 
5 === "5" // return false
```
#### Math operators
+, -, *, /, % (modulus), **(exponentiation), ++a, a++, 
JavaScript often interprets a single number inside a string as the number itself. But when we **add** a number and a string, it treats them both as strings and append them. But it only works on addition. If we use minus, JS will treat them as numbers.

## Arrays
```
const a = ["1",2,"3",4]
a.length   // 4
a[0]   // '1'
a[0] = "camera"  // can place any data type inside any slot in an array.
a[a.length] = "new item"
a[8] = "at the end"  // ['camera', 2, '3', 4, 'new item', empty × 3, 'at the end']
a[7]  // undefined
```
#### Array meethods
```
// print all items as a string, define the format by parameter
a.join()  // 'camera,2,3,4,new item,,,,at the end'
a.join(' ')  //'camera 2 3 4 new item    at the end' 
a.join(', ')  'camera, 2, 3, 4, new item, , , , at the end'
// add new items at the end
a.push("item1", "item2")
// add new items at the beginning
a.unshift("hello","hi")
// take the first item out of the array
a.shift() // the item will be returned by the shift() function
// take the last time out
a.pop()
// advanced method
a.find(function (item){if(item >1){return item}})  // using some of these array functions, we can apply new functions to the individual items within the array, or we can customize the array in pretty much any way we want.
```

## Functions
A function is a function that sits on itself, whereas a method is a function that sits inside an object and acts on that object.
```
// Function declaration:
function doSomeMath(a, b) {
  let c = a + b;
  return c;
}
// can be accidentally overrided.

// Function expression:
const doMoreMath = function (a = 3, b = 2) {
  let c = a * b;
  return c;
};
// It doesn't in itself have a name. Instead, we place it inside a variable and then we call the variable.
// It will then have the same scope as that variable type
// we can add default parameters.

// Immediately Invoked Function Expression (IIFE)
(function () {
    let a = 4;
    let b = 6;
    let c = doSomeMath(a, b);
    console.log(`The sum of a and b is: ${c}`);
})();
```
