
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



## Examples

1) Replace single value in Array without mutating it
  a) Take slice before index
  b) Concat it with a single item array with a new value
  c) Concat it with the rest of the original Array
  

  ```
  slice(0, index)
  .concat([list[index] +1])
  .concat(list.slice(index +1))

  ```
