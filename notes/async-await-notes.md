# Async Await



```js
async function createFlow(){
 console.log("Me first")
 const data = await fetch('https://twitter.com/will/tweets/1')
 console.log(data)
}
createFlow()
console.log("Me second")
```

![alt text](/img/async-await.png)


