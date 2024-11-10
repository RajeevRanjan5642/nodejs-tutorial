# nodejs-tutorial

## What is Node.js?
- Node.js is an open-source, cross-platform JavaScript runtime environment.
- Capable of executing JavaScript code outside browser.
  
## ECMAScript
- ECMA-262 is the language specification.
- ECMAScript is the language that implements ECMA-262.
- JavaScript is basically ECMAScript at its core but built on top of that.

## JavaScript Engine
- JavaScript engine is a program that converts JavaScript code into machine code that can be executed by a computer's processor.
- JavaScript engines are typically developed by web browser vendors.
  - V8 - Open-source JavaScript Engine developed by Google for Chrome.
  - SpiderMonkey - The JavaScript Engine powering Mozilla Firefox.
  - JavaScriptCore - Open-source JavaScript Engine developed by Apple for Safari.
- Node.js is built upon Google's V8 engine.

## V8 Engine
- V8 is Google's open-source JavaScript engine.
- V8 implements ECMAScript as specified in ECMA-262.
- V8 is written in C++ and is used in Google Chrome, the open source browser from Google.
- V8 can run standalone, or can be embedded into any C++ application.
- By embedding V8 into our own C++ program, we have the power to add extra functionalities like file handling, database connections and network operations in JavaScript.

## JavaScript Runtime
- JavaScript runtime is an environment which provides all the necessary components in order use and run a JavaScript code.
- A JavaScript Engine is one component in the JavaScript Runtime.
- JavaScipt Engine consists of memory and call stack.
- Chrome Browser JavaScript Runtime consists of V8 Engine, web APIs (DOM), queues, event loop etc.

## What can you build with Node.js?
- Traditional websites
- Backend services like APIs
- Real-time applications
- Streaming services
- CLI tools
- Multiplayer games

## Node.js JavaScript Runtime 
- It consists of V8, libuv, C/C++ features, JS library (core modules such as fs).
- libuv is a multi-platform support library primarily designed for asynchronous I/O operations.

## Difference b/w Node.js and Browser
- In Node.js we don't have the document, window and all the other objects that are provided by the window.
- In browser, we don't have filesystem access functionality that Node.js provides through its modules.

## Executing JavaScript with Node.js
1. using Node REPL :
   - REPL stands for Read Evaluate Print Loop.
   - It is an interactive shell that processes the instructions given by user.
     
2. Write JavaScript in a file and run it using node command in the terminal.

## Module
- A module is an encapsulated and reusable chunk of code that has its own scope.
- In Node.js, each file is treated as a separate module that is isolated by default.
- To load a module into another file, we use the require function.
- The module is loaded and cached.
- Types of modules:
  1. Local modules : Modules that we create in our application.
  2. Built-in modules : Modules that Node.js ships with out of the box.
  3. Third party modules : Modules written by other developers that we can use in our application.
- CommonJS is a standard that states how a module should be structured and shared.
- Before a module's code is executed, Node.js will wrap it with a function wrapper (IIFE) that provides module scope. This saves us from having to worry about conflicting variables or functions.
- IIFE allows us to repeat variable or function names without an conflicts.

## IIFE (Immediately Invoked Function Expression)

    (function(message){
      const superHero = "Batman";
      console.log(message, superHero);
    })('Hi');

## Module wrapper

- Every module in Node.js gets wrapped in an IIFE before being loaded.
- The IIFE that wraps every module contains 5 parameters which are pretty important for the functioning of a module.
  
      (function(__dirname,__filename,exports,module,require){
        const superHero = "Batman";
        console.log(message, superHero);
      })();

## CommonJS Modules

#### index.js
![cjs2](https://github.com/RajeevRanjan5642/nodejs-tutorial/blob/main/cjs2.png)

#### math.js
![cjs1](https://github.com/RajeevRanjan5642/nodejs-tutorial/blob/main/cjs1.png)
![cjs3](https://github.com/RajeevRanjan5642/nodejs-tutorial/blob/main/cjs3.png)

## ES Modules
- ES Modules is the ECMAScript standard for modules.
- It was introduced with ES2015.
- Instead of module.exports, we use the export keyword.

#### index.mjs
![mjs3](https://github.com/RajeevRanjan5642/nodejs-tutorial/blob/main/mjs3.png)

#### math.mjs
![mjs2](https://github.com/RajeevRanjan5642/nodejs-tutorial/blob/main/mjs2.png)

#### index.mjs
![mjs4](https://github.com/RajeevRanjan5642/nodejs-tutorial/blob/main/mjs4.png)

#### math.mjs
![mjs1](https://github.com/RajeevRanjan5642/nodejs-tutorial/blob/main/mjs1.png)

## Impoerting JSON
- JSON stands for JavaScript Object Notation.
- A data interchange format commonly used with web servers.

      {
        "name":"Rajeev",
        "Address":{
            "street":"Khara Rd",
            "city":"Bhagalpur"
        }
      }

  



