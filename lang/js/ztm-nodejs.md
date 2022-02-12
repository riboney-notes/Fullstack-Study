# ZTM's Complete Node.js Developer Course
* Link: https://academy.zerotomastery.io/

## Nodejs fundamentals

* nodejs runs javascript code outside the browser with V8engine and libuv library
* nodejs offers APIs for IO operations unlike the browser

### Node & libuv
* [node link](https://github.com/nodejs/node)
* [libuv link](https://github.com/libuv/libuv)
* `lib` folder contains the javascript code for the APIs provided in the nodejs documentation
* `src` folder contains the `C++` bindings for the javascript code in `lib`
  * things prefixed with `uv_` are references to `libuv` and javascript
  * the `uv_` implementation can be found in the `libuv` source code

### callback pattern
* [source](https://nodejs.org/en/knowledge/getting-started/control-flow/what-are-callbacks/)
* Program is "blocked" when it is waiting for some task to complete before it can complete the next task
* callback: function called at the completeion of a given task
  * prevents blocking
  * allows other code to be run in the meantime

**Example callback pattern**
```js
// typical call back convention
function asyncOperation ( a, b, c, callback ) {
  // ... lots of hard work ...
  if ( /* an error occurs */ ) {
    return callback(new Error("An error has occurred"));
  }
  // ... more work ...
  callback(null, d, e, f);
}

asyncOperation ( params.., function ( err, returnValues.. ) {
  //This code gets run after the async operation gets run
});
```
* error callback convention [source](https://nodejs.org/en/knowledge/errors/what-are-the-error-conventions/)
  * pass null as first parameter to callback function upon sucess; if error, then pass `Error` object as first paremeter

**Example error callback pattern**

```js
var isTrue = function(value, callback) {
  if (value === true) {
    callback(null, "Value was true.");
  }
  else {
    callback(new Error("Value is not true!"));
  }
}

var callback = function (error, retval) {
  if (error) {
    console.log(error);
    return;
  }
  console.log(retval);
}

// Note: when calling the same asynchronous function twice like this, you are in a race condition.
// You have no way of knowing for certain which callback will be called first when calling the functions in this manner.

isTrue(false, callback);
isTrue(true, callback);
```

### Synchronous and Asynchronous
* Synchronous code runs line by line in sequential order, waiting for the previous line to finish before moving on to the next
  * Async does not necessarily do that

* Blocking vs non-blocking
  * blocking: when execution of additional JS in node process must wait until a non-JS operation completes; Ex: synchronous methods
    * event loop is unable to continue running JS if a blocking operation occurs
  * non-blocking operations generally accept callback functions which allows it to let JS continue executing other code while waiting for blocking operations to complete; Ex: async methods like IO operations
  * to ensure correct order of operation when mixing sync and async code, throw everything in the same callback (?)

* Event loop
  * event loop allows nodejs to perform non-blocking IO operations even though JS is single-threaded, by offloading operations to the OS or threadpool
    * since most OS's are multi-threaded, they can handle multiple operations executing in the background
    * when one of the operations completes, it is moved to the poll queue to be executed
  * event loop constantly checks the call stack to see if there's any fuinction that needs to run
    * it adds function calls to the call stack and exectes each in order, until it is empty
   * functions with call backs are executed in the order they are called, but their callback functions are added into the Message queue, where it is processed only after the things in call stack are processed
   * the event loop gives priority to the call stack, and it first processed everything it finds in the call stack, and once theres nothing in there , it goes to pick up things in the message queue
   * message queue is where click/ keyboard evvents, fetch responses, etc are queued
  * Event loop phases:
    - timers
    - IO callbacks
    - setImmediate
    - close callbacks
    * each phase is responsible for a different category of events that the event loop processes
    * Each phase has their own queues of callbacks that execute during its phase
  * ES6 Job queue
    * used by promises
    * a way to execute the result of an async function ASAP rather than being put at the end of the call stack
    * Promises that resolve before the current function ends, will be executed right after the current funciton (rather than executed at the end of the call stack)

* Event Driven
  * Observer pattern
    * observer objects subscribe to subject for events
    * subject notifies all of its observers of the events that are emitted
    * observer reacts to certain events in their own way
  * In node, emitter objects of the EventEmitter class (subject) emits named events that cause listeners (observers), which are callback functions, to be called

**Event emitter example**
```js
const EventEmitter = require('events;);
// Subject:
const celeb = new EventEmitter();

// The function after 'race win' named event, is the observer/ listener

// Subscribe to celeb for Observer 1
celeb.on('race win', () => {
  console.log('Congrats!');
});

// Subscribe to celeb for Observer 2
celeb.on('race win', () => {
  console.log('Boo!');
});

celeb.emit.('race win');
```
  * process is also emitter that can emit events; Ex: `process.on('exit', (code) => {//....});`
  * You can pass parameters to listener callbacks


## Async JS

**Promises**
* Promise is an object that may produce a single value some time in the future
  * the value is a resolved value or rejected value
* Three states of promise:
  * fufilled
  * rejected
  * pending
* `Promise.all([p1, p2, p3])` can be used to executed all promises in a group and have them resolve at the same time

**Async/Await**
* An easier way to use promises
* `await` pauses whichever operation it is prefixed in front of, until the operation finishes executing (or is resolved)
* makes code look "synchronous"

**Example of Promise vs Async/Await**
```js
// promise
fetch('someurl')
  .then(resp => resp.json())
  .then(console.log);

//async-await
async function fetchUsers(){
  const resp = await fetch('someurl);
  const data = await resp.json();
  console.log(data);
}
```
**Another example of Promise vs Async/Await**
```js
const urls = [
  'url1',
  'url2',
  'url3',
];

// Promise
Promise.all(urls.map(url => fetch(url).then(resp => resp.json())))
  .then(array => {
    console.log('users', array[0])
    console.log('posts', array[1])
    console.log('albums', array[2])
  }).catch('error!');

// Async-await
const getData = async function() {
  try {
    const [ users, posts, albums ] = await Promise.all(urls.map(url => fetch(url).then(resp => resp.json())));
  
    console.log('users', users);
    console.log('posts', posts);
    console.log('albums', albums);
  } catch(err) {
    console.log('error~!', err);
  }
};
```

* You can await in a for loop of promise array

* Job Queue
  * promises are stored here
  * has higher priority than callback queue
  * event loop checks job queue first

* Parallel, Sequence, and Race
  * Parallel: execute tasks at the same time in parallel
  * Sequential: run tasks in order (first one, then second one, then third one...etc)
  * Race: run tasks but only do the one that completes first, and ignore the rest
  * EX:
  ```js
  const promisify = (item, delay) =>
    new Promise((resolve) =>
      setTimeout(() =>
        resolve(item), delay));

    const a = () => promisify('a', 100);
    const b = () => promisify('b', 5000);
    const c = () => promisify('c', 3000);

    // faster than sequence
    async function parallel() {
      const promises = [a(), b(), c()];
      const [output1, output2, output3] = await Promise.all(promises);
      return `prallel is done: ${output1} ${output2} ${output3}`
    }

    async function race() {
      const promises = [a(), b(), c()];
      const output1 = await Promise.race(promises);
      return `race is done: ${output1}`;
    }

    async function sequence() {
      const output1 = await a();
      const output2 = await b();
      const output3 = await c();
      return `sequence is done ${output1} ${output2} ${output3}`
    }

    sequence().then(console.log)
    parallel().then(console.log)
    race().then(console.log)
  ```

  * `Promise.all()` short-circuits if it encounters an error; it never returns a promise
    * `Promise.allSettled()` - does not short-circuit and will return promise containing the reject 
  
  * Browser creates one thread (call stack, heap, etc) per tab
  * webworkers work in the background
    * the are javascript program, running parallel to main thread
    * creeated with `new Worker('worker.js')`)
    * can post messages/ events to other threads
    * does not have access to window and other stuff like normal JS does
  
## Module System
* Node adds built-in function `require()`
  * it executes the javascript file and executes it and returns the results from that file
* Module
  * helps package existing code into reusuable packages
  * Helps organize your code
  * Allows for interface for code, and hides implementation 
    * code is not acccessible from module unless its exported
* `require.extensions` shows which file types node looks for when importing code
  * `.js` is the first one node looks for; as such, `.js` is not needed when importing modules
* commonjs vs ecmascript modules
  * commonjs uses require and module.exports
  * ecmascript uses import and export keywords
  * to allow for ecmascript, you have to rename the files with `.mjs`
  * file extensions are necessary for ecmascript importing
* Module caching
  * node maintains a cache (found in `require.cache` global object) of previously run modules which prevents code in those modules from being executed multiple times
    * so if some other code imports a previously imported module...then node will just check the cache and retrieve that instead of executing the module
* index.js
  * to import/export an entire folder of modules, you need a index.js inside that folder
    * allows you to treat a folder as a module, in that you can require a folder if you have a index.js inside there
  * the `index.js` imports all the modules in the folder and exports them
    * you can use spread operator to make this easy

## Packages
* Packages are collections of modules that have been packaged together
* initailize NPM package/ node project  with `npm init` which creates `package.json`
* `npm install` will create node_modules and  install packages declared in `package.json` 
  * `npm install -g` installs packages globally
* `package-lock.json` makes it easier for teams and prevents bugs because it lets you download the *exact* version of packages
* `npm audit` used for scanning packages in your project to find security issues

## Streams
* this topic is relevent to the project since it deals with parsing through large amounts of data from CSV file
* Stream is collection of data (array or string)
* Streams well-suited for working with large amounts of data
* Streams offer command piping functionality (like in bash commands)
* Many modules in node implement the streaming interface
  * HTTP res/reqs
  * file IO
  * TCP sockets
  * process stdin/stdout
  * etc
* Freecodecamp article by Samer Buna [link](https://www.freecodecamp.org/news/node-js-streams-everything-you-need-to-know-c9141306be93/)
* Unlike callbacks, streams can operate on data as it reads/comes in, instead of reading and writing data all at once

## Webservers
* Process behind web browsing
  * go to website
  * resolve webaddress with IP address by sending the url to DNS server, which looks up the IP address, and sends it back to the computer
    * only happens once...cuz the IP address is stored in DNS cache so no need to request DNS server for name resolution
  * then the IP address is used to communicate with HTTP server
    * HTTP cuz thats the protocol used to send messages back and forth
    * HTTPs is the encrypted version of it
    * the port number (the 2digit number at the end of IP address) is used to identify the application on the server to handle the request (80 for http server)
  * the web server sends back a response (HTML or json or whatever) to the computer that sent the request

## Same origin policy
* Origin
  * cominbation of protocol, host (server), port from URL
  * if any of the three elements changes, then you are no longer on the same origin
  * going to diff. pages on a website does not necessarily chane the origin since you would still be using the same host and protocol and port number
    * but going to a diff website (changing host) or changing protocol (to https) means youve changed origin
* Same Origin policy
  * security feature from browser that restricts JS from requesting/loading outside of the origin
    * ex: user and js code can make requests to same website/ host, but not to different website/ host (ex: requests to google is valid but requests to facebook are invalid when browsing google)
    * ex: `fetch('some other website);` will be denied
  * So a website can't request something from another origin; itll be denied by browswer
  * However you can be taken to another origin through HTML, but not js
  * Writes to other origins are allowed tho
    * sending data to a different website is allowed under Same origin policy
* this policy is good for protecting and keeping data on the website, and not have it be shared outside 

## CORS
  * Cross Origin Resource Sharing 
  * When a website loads and makes requests to other websites for content, this request contains a header: `access-control-allow-origin` (CORS)
    * if not, then your website can only load from same host, and outside requests will be denied
    * this header is set on response and is controlled by the webserver of the website
    * you can set to all websites or specify which outside websites are allowed (ex: allow paypal for paypal payments)
  *  Will get CORS error when having separate frontend and backend on different ports
   * to solve this, add a CORS middleware to express

## Express, Koa, and next
* Express
  * minimalistic and unopininated
  * designed to be extended with middleware
    * middleware affects routing (requests and responses)
  * Focuses on routing and high performance
  * Uses callbacks in routing
* Koa
  * Created to better make use of modern JS features
  * Uses native promises & async/await
  * More modular than express, allowing you to share middleware across projects
  * bundles res,req into single object `ctx`
  * more miniminal and better middleware extension
* Next.js
  * simplifies React integration
  * uses server-side rendering for better performance (good for search)
    * renders pages on server
    * decreases work on the browswer 
  * typescript support


## Misc
* SErving apps with Client side routing
  * when running frontend off of static website, express will try to find url endpoint or file in client that matches a url....but it wont find
    * it should instead, use index.html...but index.html is only served when url is `/`
    * the way to enable express to use index.html for other routes is to do `/*` (when doing app.use.express.static) which matches against all possible routes; obviously this code must come after router is mounted to not overwrite those routes
* Data access layer
  * Controller doesn't need to know details of the model implementation (or do need to do any processing on the data)
  * its better to abstract the details away into a data access layer
    * this can be a data access function in the model 
* Layered architecture
  * the practice of organizing an application into a set of layers like user interface, business logic, data acccess, etc
  * layer: logical structuring mechanism for the elements that make up your app
  * follows separation of concerns
* Semantic versioning: `MAJOR.MINOR.PATCH`
  * Major: when making non-backwards compatiable changes
  * Minor: when adding functionality in backwards-compatible manner
  * Patch: when making backwards compatible bug fixes
  * `^` and `~` are used to represent ranges of version number (like regex operators)
* Can POST to endpoints in dev tools console and use `fetch('url', method: 'post', payload..)`
* For express, naming file `server.js` will allow you to run that file with `npm start`
* When dealing with getting data from `req`, always validate/ test it to see if its valid
* `npm install <package> --save-dev` to use package during develop not production
* Middleware
  * middleware are functions that operate between the requests coming into webserver and the responses coming out of webserver
  * in express, middleware looks like this:
  ```js
    // pass in the function for app to use as middleware
    // next is function given by express  that invokes the next middleware, and so on until it encounters the middleware endpoint `app.METHOD`
    //   the endpoint: `get(), post()`, etc
    // once it encounters the endpoint, the direction of flow changes to send res back
    // note, next() must be invoked to pass the middleware off to the next 
    //   middleware
    // if not, then request times out
    app.use(function(req, res, next) {
      // some code...
      // end of code
      next();
    });
  ```
  * when posting dating to webserver, the format is sent in json format
    * nodejs doesn't understand json so you have to parse it
    * `express.json` is middle

* in route handling funtions, once you set or send `res`, you can't do it again later in the function

* Model View Controller MVC
  * pattern that splits code into model, view, and controller
  * User uses controller, controller manipulates model, model updates view, user sees view
  * since controller is directly associated with routes, they live in the same folder

* Using named functions is good because then node can tell you where some error originated from 
  * good for debugging

* You can set custom middleware for specific routes by doing `xxxRouter.use(...)` with the router object

* REST
  * collections of data should be named with plural noun
  * RESTFUL apis are those that follow a certain pattern/ standard/ guidelines when using HTTP APIS
  * Deals with how data is represented and how it is transferred
  * Use existing standards HTTP, JSON, URL
  * Endpoints are colection of data
  * Use GET, POST, PUT, and DELETE
  * Client and server architecture
  * Requests are stateless and cacheable
    * each request is separate and not connected to any state on the client thats not included in the request
      * server does keep track of which requests user has made in the session
      * data on server is separate from client
      * client could open new browser and use the REST api to get the same data
      * opposite of stateless would be an API that tracks user in a session which sticks around during requests 
      * only request keeps track of state (not client or server) whihch means requests results can be cached for future use without having to go through the process of geting those results for those requests
      * this increases performance
      * example results from `GET /friends` request wuold be cached and not looked up if the request is made again

* to use node to serve static pages, use `express.static(..path to html/css/js folder)
  * not good for performance
  * better to use CDN to serve static files (like Akamai)

* its good to have separate package.jsons for different parts of the applications like server, client, and the root project folder
  * the node_modules folder will be in root
  * the root package.json will interact with the other package.jsons

## Basic Express project setup
* Main Folders
  * Client folder for frontend
  * Server folder for API
  * package.json for each folder
  * project root json file also (?)

* `npm i --save-dev nodemon` to install nodemon as dev dependency (so it doesn't get included in production)
  * set to `watch: nodemon src/server.js`

* Create `server.js` that only has `http` and listens to server with `app` from express
  * Ex:
  ```js
  // allows us to handle HTTP as well as other types (ex: sockets)
  const http = require('http');
  const app = require('./app'); // Express
  const server = http.createServer(app);
  server.listen(PORT, ()=>{console.log('running')});
  ```

* Create `routes` folder that groups together related routers and controllers in subfolders
  * why controllers and routers are together?
  * because they are one to one (one router for one controller)
  * models on the other hand are many, thus would be better off in their own folder

* `app.js` is the folder that handles all the express stuff
  * sets up middleware, ex: `app.use(express.json())` 
  * mounts routers


* remember to always *return* in a controller/ router handler function to prevent error
  * express doesn't use the return value....setting the res is whats needed
  * but, by returning, you make sure to terminate the function and prevent it from seting header again which will cause error

## Streams and node
* so when dealing with streams, node will export the data before the streams have completed processing
* thus, you need to use promises to wait for the processing to be complete
* there is streams promises API that you can use or you can wrap the stream operation in a promise yourself

## automating fullstack with root package.json
* can perform running of client and server in the root project from the root package.json file
* EX:
```json
    "server": "cd server && npm run watch",
    "client": "cd client && npm start",
```
* Another way is to use the `--prefix` which will run the command in the folder from arg for prefix
```json

```

* to run both commands, do `"watch": "npm run server & npm run client",`
  * why `&` and not `&&`? Because with `&&` the first command runs and does not exit, thereby preventing the second one from running; with `&` the first one runs the background allowing the second to run
  * use `&&` for commands that exit, like: `"install": "npm run install-server && npm run install-client",`
    
## Production
* In develop, you run client and server on different ports
  * but in prod. you'll want to run them on same server, same port 
* to enable running client and server in same server, first build the client by running the build script and direct the build path to the server
  * the resulting public folder will contain the static code for nodejs/ express to serve (with `app.use(express.static(__dirname, ''..', 'public))`)
  * example: `"build": "BUILD_PATH=../server/public react-scripts build"`
  * the build folder will contain `public` folder and bundle everything into that folder and minimize load time
  * then do `app.get('/', (req, res) => {res.sendFile(index.html)})` to send that index.html from the public folder
  * then you can run the backend sever, and it will run the frontend
  * use the deploy script in root package.json file: `"deploy": "npm run build --prefix client && npm start --prefix server"`

## Maps vs objects
* So in objects, you can only set strings as keys 
* In maps, you can set anything as keys and have it be associated with value
  * Ex: `{1234: new SomeObjet()}`....
  * you can even set functions as keys to values
* maps are alot more flexible
* Preserves order of keys being inserted
  * you get keys:values in the order they were in
  * unlike objects when you go through the keyset
* However, maps are not JSON\
  * use the `values()` to get list of values as iterable, which would then need to be converted into Array
