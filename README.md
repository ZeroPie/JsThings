# Javascript-Reference
Just a Reference to look into with the correct Terms that i keep forgetting 


### Compile Time
1. Scope Managing
1. LeftSide(Target of Assignment) | RightSide (Source) declaration

### Interpretation Time

1.
1.



### Implicit Global Variable Creation (Dont do this)

After Compile at Runtime 
```js
function wat() {
    lulz = 'imglobalnow lulz'
}
```
Implicitly create a Global as a result of assigning to a variable that was never declared:

Fix:
1. Dont do it (it's bad and slower to create a var at runtime)
1.'use strict' => reference Error is then thrown

### Shadowing ###

```js
var wat = 'wat'

function watify() {
    console.log(wat) => undefined
    var wat = 'this will be shadowed at compile time, r.i.p accessing this lexically at runtime (screw window.wat which only works because we are one level deep)'
}
```




Move this to a different File:

### Computed Property Names in Objects:

```js
const obj = {
    [action.name]: action.payload
};
```


