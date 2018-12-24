## Computed Property Names in Objects:

```js
const obj = {
    [action.name]: action.payload
};
```

## Destructuring

### Destructuring Objects
```js
state = {
  hot: false,
  cool: true,
  destructured: 'destructured'
}
const { destructured, cool } = this.state

`Element is ${this.state.hot} and ${destructured} and ${cool}`
```

Rename Properties

```js
const stuff = { x: 'x', y: 'y', z: 'z'}
const { x:anotherName } = stuff
console.log(anotherName)
```
Better Name?

```js
let {x: ten, girl: problem, solution: SOLUTION} = {x: 10, girl: 'grill', problem: 'chill'};

console.log(ten, problem, SOLUTION); //10, grill, chill
```

### Assign Default Values
```js
const { wat = 'wat', active = false } = { wat:0 }
```

### Destructuring and Default Values in Function Signatures
```
const funWithDefault = ({ initialValue = 0, isActive = false } = {}) => {
  console.log(`initialValue: ${initialValue} isActive: ${isActive}`)
}

funWithDefault({}) // => 0, false
funWithDefault({initialValue: 1}) // => 1, false
funWithDefault({initialValue: 1, isActive: true}) // => 1, true
```

### Destructuring Arrays:
```js
const [a,b] = [1,2] // Position does matter
console.log(a,b) // => 1,2 
```


### Named and Optional Arguments 

```js
  const fun() => ({ 
  
  })
```
