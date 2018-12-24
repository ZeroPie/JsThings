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
