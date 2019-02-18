# Javascript-Reference
Just a Reference to look into with the correct Terms that i keep forgetting 

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

Not truly a thing, it's a way to think about the 2 pass compilation process in JS
Vars and lexical scopes are parsed
Values are then assigned
Thats why we can declare a var after already haven given it a value and that stuff works


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

##Primitive Types

1. undefined
2. string
3. number
4. boolean
5. object
6. symbol

---
- function (subtype of object, it's a callable object)
- null (no identity aka null !== typeof null)

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
| ""          |   0         | wtf
| "0"         |   0         | 
| "-0"        |   -0        |
| " 009 "     |   9         |
| "3.14159"   |   3.14159   |
| "0 ."       |   0         |
| ".0"        |   0         |
| "."         |   NaN       |  wtf
| false       |   0         |
| true        |   1         |
| null        |   0         |  wtf
| undefined   |   NaN       |  wtf
