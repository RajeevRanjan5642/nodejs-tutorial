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
  
## libuv
- libuv is a cross platform open source library written in C language which handles asynchronous non-blocking operations in Node.js using thread pool and event loop.
- The CPU intensive tasks (CPU bound operations) such as file operations, password hashing are offloaded to libuv's thread pool from main thread to avoid blocking the main thread. They run on separate threads parallely in libuv's thread pool.
- libuv's thread pool has 4 threads by default.
- We can increase the thread pool size :
  
      process.env.UV_THREADPOOL_SIZE = <size>;
  
- If we increase the thread pool size beyond the no. of CPU cores, then the time to execute each thread increases significantly since os has to switch b/w the threads in order to provide each thread an equal amt. of CPU time.
- Hence increasing the thread pool size can help improve the performance but is limited by the no. of available CPU cores.

## Code Execution in Node.js

![code](https://github.com/RajeevRanjan5642/nodejs-tutorial/blob/main/Screenshot%202024-11-11%20200320.png)

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

### fs module
- fs module allows us to work with file system on our computer.

      const fs = require("node:fs");
      
      const data = fs.readFileSync("./test.txt", "utf-8");
      console.log(data);
      
      fs.readFile("./test.txt", "utf-8", (err, data) => {
        if (err) console.log(err);
        else console.log(data);
      });
      
      fs.writeFileSync("./greet.txt", "Bonjour");
      
      fs.writeFile(
        "./greet.txt",
        "Good Morning",
        /*{flag:"a"},*/ (err) => {
          if (err) console.log(err);
          else console.log("file written");
        }
      );

### fs promise module

      const fs = require("node:fs/promises");
      
      fs.readFile("./greet.txt", "utf-8")
        .then((data) => console.log(data))
        .catch((err) => console.log(err));

async-await

    const readFile = async () => {
      try {
        const data = await fs.readFile("./greet.txt", "utf-8");
        console.log(data);
      } catch (err) {
        console.log(err);
      }
    };
    
    readFile();

## Streams

    const fs = require("node:fs");
    
    const readableStream = fs.createReadStream("./greet.txt",{
        encoding:'utf-8',
    });
    
    const writableStream = fs.createWriteStream("./greet2.txt");
    
    // readableStream emits a data event
    readableStream.on("data",(chunk)=>{
        console.log(chunk);
        writableStream.write(chunk);
    });

## Pipes
- connects a readable stream to a writable stream.

      const fs = require("node:fs");
      
      const readableStream = fs.createReadStream("./greet.txt",{
          encoding:'utf-8',
      });
      
      const writableStream = fs.createWriteStream("./greet2.txt");
      
      readableStream.pipe(writableStream);

  ### HTTP Module
  - The HTTP module allows creation of web servers that can transfer data over HTTP.
    
        const http = require("node:http");
        
        const server = http.createServer((req, res) => {
          res.writeHead(200, { "Content-Type": "text/plain" });
          res.end("Hello World");
        });
        
        server.listen(3000,()=>{
            console.log('Server is listening on port 3000');
        });

- JSON response

      const server = http.createServer((req, res) => {
        const superHero = {
          firstName: "Bruce",
          lastName: "Wayne",
        };
        res.writeHead(200, { "Content-Type": "application/json" });
        res.end(JSON.stringify(superHero));
      });

- HTML response

      const server = http.createServer((req, res) => {
        res.writeHead(200, { "Content-Type": "text/html" });
        res.end("<h1>Hello World</h1>");
      });

      const server = http.createServer((req, res) => {
        res.writeHead(200, { "Content-Type": "text/html" });
        fs.createReadStream(__dirname+"/index.html").pipe(res);
      });

- HTTP Routing

      const http = require("node:http");
      
      const server = http.createServer((req, res) => {
        const url = req.url;
        switch (url){
          case '/':
              res.writeHead(200,{'Content-Type':'text/plain'});
              res.end('This is home page.');
              break;
          case '/about':
              res.writeHead(200,{'Content-Type':'text/plain'});
              res.end('This is about page.');
              break;
          default:
              res.writeHead(404,{'Content-Type':'text/plain'});
              res.end('Page not found');
        }
      });
      
      server.listen(3000, () => {
        console.log("Server is listening on port 3000");
      });

## Web Framework
- A framework simply abstracts the lower level code allowing you to focus on the requirements than the code itself. For example, Angular, React, Vue are all framework/libraries that help you build user interfaces without having to rely on the lower level DOM API in JavaScript.

- There are frameworks to build web or mobile applications without having to rely on the HTTP module in Node.js. For e.g. express,nest,hapi,koa,sails. 

-They are built on top of the HTTP module making it easier for you to implement all the features.

## Single-threaded
- A thread is simply a process that your javascript program can use to run a task.
- Each thread can only do one task at a time.
- JavaScript has just the one thread called the main thread for executing any code.
