
State: Minimal Representation of Data in your App

Action: Minimal Representation of Change to that Data

How to Change State ? 
You Dispatch an Action

Components only know they have to dispatch an action. 


Pure Functions (do not modify items or have side effects)
Concrete examples: 


| Dont           | Do           |
| ---------------|:-------------:|
| list.push(0)    list.concat([0])
No Push instead Concat
No SPlice instead Slide 




Reducer (pure function): (previous state, action) => return new state
Takes the previous state and action being dispatched and returns the NEW STATE



Filter: Show all open
close all
open all

