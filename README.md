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
    var wat = 'shadowed" // Wat will be shadowed at compile time, 
    r.i.p accessing this lexically at runtime (screw window.wat, 
    btw it only works because we are one level deep, 
    but with more nesting it wouldnt)
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
