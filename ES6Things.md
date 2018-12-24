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
let {x: ten, girl: problem, solution: SOLUTION} = {x: 10, girl: 'grill', problem: 'chill'};

console.log(ten, problem, SOLUTION); //10, grill, chill
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
