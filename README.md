# JavaScript

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



#### javaScript in an HTML document
The script tag can be placed anywhere within the HTML document. Technically speaking, you would want to place it in the head section because it's a meta part of the document, and it's npt part of the actual document . But in many cases, script tags are always placed at the very end of the document. Browser read HTML from the top, line by line. It renders it out as it reads it and then anytime it encounters JavaScript everything stops that's because the JavaScript may make changes to the document, and then reads all the JavaScript. renders the JavaScript and thne goes back to the rendering the entire page.

#### JavaScript as an external file
<script src="script.js"></script>

#### Modern JavaScript loading
async and defer keywords: tightly control how and when JavaScript is loaded, and they need a bit of explanation. 

##### Default behavior: (reference a script and point to the file)
The browser start parsing the HTML document, up until the point where it finds this reference, then it **stop parsing the HTML**, goes **downloads the js file**, then **executes whatever is in the js**, then picks up the HTML parsing. It is called content or render blocking.
##### Async keyword:
When meets a js, **keep parsing the HTML while download the js**, **only stop parsing when you actually have the file**, then executes whatever's in the js, then continue HTML parsing. 
##### Defer keyword:
Tells browser that parse HTML and if you encounter js, just **load js alongside your HTML parsing**, then **when the HTML parsing is complete, execute whatever js you have**.
<script src="script.js" **defer**></script>

Loading Js in the footer, is now an anti-pattern. JavaScript should always be loaded in the head, and then use async or defer, to control when that Js is executed on the document.

