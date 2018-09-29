
## Terms
- State: Minimal Representation of Data in your App
- Action: Minimal Representation of Change to that Data
- Reducer (pure function): (previous state, action) => return new state
Takes the previous state and action being dispatched and returns the NEW STATE

## Principles

### How is State Changed? 
You Dispatch an Action

- Components only know they have to dispatch an action. 

### Use Pure Functions (do not modify items or have side effects)
Concrete examples: 


| Dont                   | Do                   |     Do (ES6)                    | 
| ---------------------- |:--------------------:|---------------------------------|
| Pre E6                 |                      |    ES6(Spread Operator)         |
| ```list.push(0)```     | ```list.concat([0]```| ```[...list, 0]```              |
| ```splice(index,1)```  | ```slice(0, index)```| ```[...list.slice(0, index)]``` |  

### Avoid Object Mutations

| Dont                   | Do                                  | 
| ---------------------- |:--------------------:               |
|                        |                                     | 
| <pre> todo.completed =! todo.completed <br>return todo;<br> </pre>   | ```return Object.assign({}, todo, {completed: !todo.completed })```|



## Examples

1) Replace single value in Array without mutating it  
  ```
  
  slice(0, index)               //Take a slice before the index
  .concat([array[index] +1])     // Concat it with a single item array with a new value
  .concat(array.slice(index +1)) // Concat it with the rest of the original Array

  ```
