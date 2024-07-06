# Iterators

Iterators are functions which return out the next element of the stream of data (a collection of data. E.g. array) without need of manually getting the next element.

Iterators turn the collection of data into a stream of values that we can access one after anotehr.

Iterators automate the process of accessing the element, so we can focus on what we can do to each element.

Generators dynamically control the values that come out of that flow.



### Example - For loop

For loop is an example of manually getting the next element from a collection of data.

```js
const numbers = [4,5,6]
for (let i = 0; i < numbers.length; i++){
 console.log(numbers[i])
} 
```

![alt text](/img/for-loop.png)



### Example - 2

```js
function createNewFunction() {
 function add2 (num){
 return num+2;
 }
 return add2;
}
const newFunction = createNewFunction()
const result = newFunction(3)
```
![alt text](/img/example-2.png)


### Example


```js
function createFunction(array){
 let i = 0
 function inner(){
 const element = array[i]
 i++
 return element
 }
 return inner
}
const returnNextElement = createFunction([4,5,6])
```

![alt text](/img/iterator.png)