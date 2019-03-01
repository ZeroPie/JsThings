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

### Nested Destructuring

```js
    const { a, 
            b, 
            c: { n } = {} // provide a default in case it doesnt exist :)
            } = obj
```

```js
    const { a, 
            b, 
            c: [ n ] = [] // provide a default in case it doesnt exist :)
            } = obj

```

### Mixed Nested Destructuring Arrays in Objects

```js
const result = {
  location: 'Köln',
  categories: [
    {
      name: 'eisdielerina',
      adresse: 'bonner str',
      type: 'gastro'
    }
  ]
}

const getCategoryName = ({
  categories: [{name}]  
}) => ({
  name
})

getCategoryName(result) // 'eisdielerina'
   
```



### Rename Properties

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

## Destructuring and Default Values in Function Signatures

```js
const illbeZeroIfYouDontGiveAParam = (n = 0) => n;
// => 0
```

### Named and Optional Arguments 

```js
const funWithDefault = ({ initialValue = 0, isActive = false } = {}) => {
  console.log(`initialValue: ${initialValue} isActive: ${isActive}`)
}

funWithDefault({}) // => 0, false
funWithDefault({initialValue: 1}) // => 1, false
funWithDefault({initialValue: 1, isActive: true}) // => 1, true
```

### Nice Little Pattern 

```js
const foo = () => ({ a:1, b:2, c:3 })

const {a : first, b} = foo() || {};
console.log(first) // 1
```

Alternative with Object Ref
```js
const foo = () => ({ a:1, b:2, c:3 })
let retObj;
const {a : first, b} = retObj = foo() || {};
```

### Destructuring Arrays:
```js
const [a,b] = [1,2] // Position does matter
console.log(a,b) // => 1,2 
```

## Rest And Spread

### Tail and Head in Arrays

```js
const getTail = (head, ...tail) => tail;
getTail(1, 2, 3); // [2, 3]

const getHead = arr => head(arr) // 1 ( ͡° ͜ʖ ͡°)  

```


```js
const shiftToLast = (head, ...tail) => [...tail, head];
shiftToLast(1, 2, 3); // [2, 3, 1]
```

### Gather or Spread ?

```js
left side          |  right side
assignment context |  declaration context
...gather = ...spread

```

### Nice Pattern for Arrays

```js
const f = () => [1,2,0,3]

var [
    a = 1,
    b,
    c,
    ...args
    ] = f() || [] // in return is null we stil get an empty Array
```
We can also destructure into object properties

```js
const f = () => [1,2,0,3]
const ob = {}
var [
    ob.a = 1,
    ob.b,
    ob.c,
    ...ob.args
    ] = f() || [] // in return is null we stil get an empty Array

```

Examples:

Dump:
```js
const ar = [1,2,3]
let d;

[ d, d, ...a] = [0, ...a, 4] // a => 2,3,4
//similar to
[ , , ...a] 
```

## Let

```js
function tralala () {
    
    { // scope
        let id;
    }
}
```

## Generators

'Interruptable/pausable' functions

Syntactic form to declaring a state machine

Localized blocking (only inside the generator, not the entire program)

Sync: A way to produce an iterator



### yield (pause)

It's okay not to consume a generator fully, they don't have to finish and will get garbage collected

```js

function* gen() {
  console.log('Hello')
  yield // The generator decides when to pause
  console.log('World')
}

var it = gen()  // none of the generation runs, it just produces an iterator
it.next() // Hello
it.next() // World

```


### Consume an iterator

for of loop


