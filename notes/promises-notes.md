# Promises

Promises do two things:
1. Outside the JS, in the Web Browser they start some background web browser feature.
2. Simultaneously in JS produces a Promise Object that will be returned immediately. A Promise Object is a placeholder, and has a property on it - Value. Value property initially has nothing, but it is going to be filled automatically later, when the background web browser task finishes. 
  - To sum up: in the returned Promise Object, a Value property will be automatically filled when a web browser task is finished.
  - It will have a hidden property OnFulfillment that will have a functionality that will be triggered automatically in JS when that value gets updated.
  - Value will be attached functionality's argument.


Promises act as a placeholder for the data we hope to get back from the web browser feature's background work.




fetch - not JS feature. It is a Web Browser feature.  
      - It starts a Web Browser feature - XMLHttpRequest (XHR).

Function 'display' was deferred by a Promise and then it gets back in the JS to be run.



Functions, that use a Web Browser Feature and don't return  anything in the JS (that don't return a Promise Object in the JS) gets pushed in the Callback Queue.

Other functions, that get automatically triggered when the Value property is filled, get pushed in the Microtask Queue.


The Event Loop prioritizes tasks in the Microtask Queue.



OnFulfillment array holds functions that will be executed if the promise is resolved.  
OnRejection array holds functions that will be executed if the promise is rejected.



A live data (labels, values) that is stored in the application is called a State.









### Example - 1

```js
function display(data){
 console.log(data)
}
const futureData = fetch('https://twitter.com/will/tweets/1')
futureData.then(display); // Attaches display functionality
console.log(“Me first!”);
```
![alt text](/img/promises-1.png)


### Example - 2

```js
function display(data){console.log(data)}
function printHello(){console.log(“Hello”);}
function blockFor300ms(){/* blocks js thread for 300ms with long for loop */}
setTimeout(printHello, 0);
const futureData = fetch('https://twitter.com/will/tweets/1')
futureData.then(display)
blockFor300ms()
// Which will run first?
console.log(“Me first!”);
```

![alt text](/img/promises-2.png)