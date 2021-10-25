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
  
##### object container
const: constant. Objects are typyically constants: we can change the properties of the object inside the container. We can't remove or replace the object from the container. 
##### object properties
property name can only contain letters, digits, dollar signs and underscores. 
