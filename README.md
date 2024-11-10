# Node.js

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
  2. Built-in modules : Modules that Node.js ships with out of the box. They are also known as core modules.
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

## JSON
- JSON stands for JavaScript Object Notation.
- A data interchange format commonly used with web servers.

      {
        "name":"Rajeev",
        "Address":{
            "street":"Khara Rd",
            "city":"Bhagalpur"
        }
      }

## Built-in Modules

### Path Module 
- provides utilities to work with files and directories.

        const path = require('node:path');
    
        console.log(path.basename(__filename));
        console.log(path.basename(__dirname));
        console.log(path.extname(__filename));
        console.log(path.parse(__filename));
        console.log(path.isAbsolute(__filename));
        console.log(path.join(__dirname,'data.json'));
   
## Callbacks
- In JavaScript, functions are first class objects.
- A function can be passed as an argument.
- A function can be returned as values from other functions.
- A function that is passed as an argument to another function is called a callback function.

      function greet(name){
          console.log(`Hi ${name}`);
      }
      
      function higherOrderFunction(callback){
          const name='Linda';
          callback(name);
      }
      
      higherOrderFunction(greet);

- Asynchronous callback : A function that is executed after an asynchronous operation is finished.
- For e.g. reading from a file, fetching data from database etc.
- Node.js have an asynchronous nature to prevent blocking of execution.

### Events Module
- The events module allows us to work with events in Node.js.
- An event is an action or an ocuurence that has happened in our application that we can respond to.
- Using the events module, we can dispatch our own custom events and respond to those custom events in a non-blocking manner.

      const EventEmitter = require('node:events');
  
      const emitter = new EventEmitter();

      // event listener
      emitter.on('order-pizza',(size,topping)=>{
          console.log(`Order received! Baking a ${size} pizza with ${topping}.`);
      });
      
      emitter.on('order-pizza',(size)=>{
          console.log(`Serving a complementary drink!`)
      })

      // dispatch an event
      emitter.emit('order-pizza','large','mushroom');

  ## Character set & encoding
  - Computers store and represent data in binary format which is a collection of 0s and 1s.
  - To work with a piece of data, a computer needs to convert that data into its binary representation.
  - In case of characters, computers will first convert the character to a number, then convert that number to its binary representation.
  - Character Sets are predefined lists of characters with their numeric representation.
  - Popular character sets - Unicode and ASCII
  - Character encoding dictates how many bits to use to represent the number.
  - Example of a character encoding system is UTF-8.
  - UTF-8 states that 8 bits should be used to represent the code of any character in binary.
 
  ## Streams & Buffers
  - A stream is a sequence of data that is being moved from one point to another over time. for e.g. a stream of data over the internet being moved from one computer to another.
  - Process streams of data in chunks as they arrive instead of waiting for the entire data to be available before processing.
  - Node.js cannot control the pace at which data arrives in the stream. It can only decide when is the right time to send data for processing. If there is data already processed or too little data to process, Node.js puts the arriving data in buffer.
  - Buffer contains raw binary data.
 
        const buffer = new Buffer.from("Rajeev");

        buffer.write("code");
        
        console.log(buffer.toJSON());
        console.log(buffer);
        console.log(buffer.toString());


