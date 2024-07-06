# Generators

With Generators we can set what individual element will be returned next.

Built in iterators produce an object with two properties on it:
- value - The next value in the iteration sequence. The value that the function returns out.
- done - A boolean indicating whether the iteration is complete. 
  - 'done: false' until there is another value to yield. The 'value' property contains the next value in the sequence.
  - 'done: true' iterator has completed the sequence and there are no more values to yield. The 'value' property is typically 'undefined' (although it can technically hold any value).



'yield' keyword suspends the execution context and exits out of the function.

### Example - 1

```js
function createFlow(array){
 let i = 0
 const inner = {next :
 function(){
 const element = array[i]
 i++
 return element
 }
 }
 return inner
}
const returnNextElement = createFlow([4,5,6])
const element1 = returnNextElement.next()
const element2 = returnNextElement.next()
```

![alt text](/img/generators-1.png)



### Example - 2


```js
function* createFlow(){
 yield 4
 yield 5
 yield 6
}
const returnNextElement = createFlow()
const element1 = returnNextElement.next()
const element2 = returnNextElement.next()
```

![alt text](/img/generators-2.png)



### Example - 3


```js
function* createFlow(){
 const num = 10
 const newNum = yield num
 yield 5 + newNum
 yield 6
}
const returnNextElement = createFlow()
const element1 = returnNextElement.next() // 10
const element2 = returnNextElement.next(2) // 7
```

![alt text](/img/generators-3.png)




### Example - 4


```js
function doWhenDataReceived (value){
 returnNextElement.next(value)
}
function* createFlow(){
 const data = yield fetch('http://twitter.com/will/tweets/1')
 console.log(data)
}
const returnNextElement = createFlow()
const futureData = returnNextElement.next()
futureData.value.then(doWhenDataReceived)
```

![alt text](/img/generators-4.png)




