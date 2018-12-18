# Javascript-Reference
Just a Reference to look into with the correct Terms that i keep forgetting 

### Computed Property Names in Objects:

```js
const obj = {
    [action.name]: action.payload
};
```

### Implicit Global Variable Creation

DONT: Implicitly create a Global as a result of assigning to a variable that was never declared:
Fix: dont do it or 'use strict' => reference Error is then thrown

After Compile at Runtime 
```js
function wat() {
    lulz = 'imglobalnow lulz'
}
```

### Shadowing ###

```js
var wat = 'wat'

function watify() {
    console.log(wat) => undefined
    var wat = 'this will be shadowed at compile time, r.i.p accessing this lexically at runtime (screw window.wat which only works because we are one level deep)'
}
```


