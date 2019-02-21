# Javascript-Reference
Just a Reference to look into with the correct Terms that i keep forgetting 


WIP:
1) Todo create index
2) Split into sections


### Terminology
1. Object Literal ``const obj = {}``
1. Array Literal ``const arr = []``



### Compile Time
1. Scope Managing
1. LeftSide(Target of Assignment) | RightSide (Source) declaration

``` js
function wat() {
    var wth = 'wth'
}
wat() // Right Hand Side Value (Source Declaration)
```

1. go resolve the wat expression and find out its value (in this case a function 
2. go to the parenthesis () - almost as if they were operators - and execute 


Lexical Scope is fixed (at compile time)

```
this var is always reference 
```

Formal Declaration
```
var functionDeclaration = 'identifier'

function wat(formal declaration for a parameter)
```

### Interpretation Time / Execution
All Variable and Function Declarations have been compiled away

```diff
- var omg = 'omg'
wat() {
-   var wat = 'wat'
    dahell () {
    }
}
wat()
```


### Implicit Global Variable Creation (Dont do this)

After Compile at Runtime 
```js
function wat() {
    lulz = 'imglobalnow lulz'
}
```
Implicitly create a Global as a result of assigning to a variable that was never declared:

Fix:
1.  Dont do it (it's bad and slower to create a var at runtime)
1. 'use strict' => reference Error is then thrown


btw: Global Vars are not created for functions <3
```
wth() // reference error
```


### Shadowing ###

```js
var wat = 'wat'
function watify() {
    console.log(wat) => undefined
    var wat = 'shadowed' // Wat will be shadowed at compile time, 
    r.i.p accessing this lexically at runtime ( window.wat would
    work if we are one level deep, but with more nesting it wouldnt)
}

```

-----------

### Function Declaration

```js
function declaration() {}
```



### Anonymous Function Expression

```js
var clickHand = function {}
```


### Named Function Expression

```js
var named = function declaration () {
    declaration() // is now available within its own scope
}
```
Always prefer Named Function Expressions over Anonymous Function Expressions
1. Reliable and Handy function self-reference (identifier is read only)
2. Debuggability: Uses name in stack trace
3. Code Readability 


### Lexical Scope

Predictable 
```js
    
function fx () {
    var lc = 'lc'
    function x () {
        console.log(lc) // lexical, aka always bound to scope 
    }
    lc()
}
fx ()
   
```


### Dynamic Scope
Flexible: Function resolves references to variables dynamically depending on where it is called
Theoretical Example:
```js
function wat() {
    console.log(sc)
}

function sc () {
    var sc = 'ss'
    foo();
}

sc(); // ss
    
```


## Closure

Ability of a Function to 'remember' its lexical scope, even when it is executed outside its lexical scope

## Hoisting

Not truly a thing: It's actually a way to think about the 2 pass compilation process in JS.
1) Vars and lexical scopes are parsed
2) Values are then assigned
Thats why we can declare a var after already haven given it a value and that stuff works

let and const behave differently


## New Keyword (constructor call)

```
var foot = new shoot();
```
1. A brand new Empty Object is created
1. The newly created object is linked to another Object
1. The newly created object is passed in as the this context to the function call
1. Imply that it return this (itself)

### Rules of order of precedence:
Whats this going to point to

1. new (yup, it overrides bind)
2. call()/apply() (bind() uses apply()
3. context object (o2.foo()) 
4. default: global object (except strict mode)


## Thunks

A function with closure state that keeps track of some value and it gives you those back when you call it

### Synchronous Thunk

```js
function add(x, y) {
    return x + y
}

var thunk = function() {
    return add(10,15);
}

thunk(); // 25
```


### Asynchronous Thunk

Fn doesnt need arguments except the callback to get the value out

From outside we don't care or know wether the value is there immediately or if we have to wait
We pass the callback and the callback is called when a value is ready
Eliminates time as a factor
Give Callback get value out


```js
function addAsync(x,y,cb) {
    setTimeout(function(){
        cb(x + y)
    }, 1000);
}

var thunk = function(cb) {
    addAsync(10,15,cb);
}

thunk(function(sum){
    sum; //25
});

```


```js
function getFile(file) {
  var text, callback;
  asyncRequest(file, function(response){
    if (fn) fn(response);
    else text = response;
  })

  return function(callback){
    if (text) callback(text);
    else fn = callback;
  }
}

var thunk1 = getFile('file1')
var thunk2 = getFile('file2')
var thunk3 = getFile('file3')

thunk1(function(text1) {
  console.log(text1)
  thunk2(function(text2){
    console.log(text2)
    thunk3(function(text3){
      console.log(text3)
      console.log("Complete")
    })
  })
})

```
# Coercion

## Primitive Types

1. undefined
2. string
3. number
4. boolean
5. object
- function (subtype of object, it's a callable object)
- null (no identity aka null !== typeof null)
6. symbol

## Special Types
- NaN
- Infinity, -Infinity
- null
- undefined (void)
- +0, -0

## Nan
``` js
var a = 'a' / 2

a          // NaN
typeof a  // "number"

isNan('foo') // true WTF => tries to convert it to a number first and then checks if its a Number
```

## Native(s) (Functions)

- String()
- Number()
- Boolean()
- Function()
- Object()
- Array()
- RegExp()
- Date()
- Error()

## toString

  
| Value            |  Result       |  
| -----------      | ------------- |
| null             |  null         |
| undefined        |  "undefined"  |
| 3.14159          |  "3.14159"    |
|  0               |  "0"          |
| -0               |  "0" //WTF    |
| []               |   ""          |
| [1,2,3]          |  "1,2,3" //no brackets :(|
| [null, undefined]|   ","  //WTF  |
| [[[],[],[]],[]]  |   [,,,]       |
| [,,,,]           |   ',,,' //trailing comma|
|  {}              |  "[object Object]"   |
|  {a:2}           |  "[object Object]"   |

## toBoolean

| Falsy       | Truthy        |  
| ----------- | ------------- |
| ""          |   "foo"       |
| -0, 0, +0   |   23          |
| null        |   {a:1}       |
| NaN         |   [1,3]       |
| false       |   true        |
| undefined   |function(){...}|


## toNumber 

| Value       | Result      |
| ----------- | ----------- |
| ""          |   0 //WTF   | 
| "0"         |   0         | 
| "-0"        |   -0        |
| " 009 "     |   9         |
| "3.14159"   |   3.14159   |
| "0 ."       |   0         |
| ".0"        |   0         |
| "."         |   NaN //WTF |  
| false       |   0         |
| true        |   1         |
| null        |   0 //WTF   |  
| undefined   |   NaN //WTF |  




## +

```js
var foo = '123'
baz = +foo
baz // 123
```

## * --> boolean

### Boolean()

```js
var baz = Boolean(foo)
```

### !! (double negate operator)
! negate operator
! coerce to a boolean (toBoolean()) and flips the parity (!negate operator) 
! flip it back
```js
baz = !!foo;
```

### Ternary Operator

```js
baz = foo ? true : false
```


## Date

```js
Date.now()
// var now = +new Date()
// var foo = 'foo'

var now = new Date // works too shrugs*
```
## ~

``` js
// indexOf returns a number
~foo,indexOf('f') //-1 => // N -> -(N+1)
```

## Boxing

Js automatically coerces a primitive to its object wrapper counterpart (in this case Number:)
That is why we can use .toString() without casting it to a String Object
```js
baz = 456;
foo = baz.toString();
foo // '456'
```



## Recommendation

Dont user new String() new Number () 
They create object

new String () => Dev Console String in italics
new String () => wrapper object around the primitive String => Object

As function
String () doesnt wrap, it just coerces


0 primitive is truthy
0 as Obj

false as Boolean primitive is falsy
false as Boolean object is truthy


```js
new Array(42) // overloaded => now this is the length
sparse Array => empty array => array.length console: 42
map => they dont exist, empty/phantom slots

```


JS doesn't allocate memory, creates a linked list and sets the lenght to 42 
no perfomance benefit


```js
use the literal
imperative - declarative
new Object() <=> { a: 1, b: 2}
```

Regexp
```js
foo  = new RegExp("a*b", "g") // use if it the pattern has to be dynamic
foo = /a*b/g
```



