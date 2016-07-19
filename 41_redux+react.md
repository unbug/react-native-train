# 4.1 [Redux](http://redux.js.org/)

1.Actions & Action Creators

![](QQ20160719-2.png)

```
//action type
const ADD_TODO = 'ADD_TODO';

//action creator, semantic methods that create actions
//collected together in a module to become an API
function addTodo(title, hour) {
  //action, an object with a type property and new data, like events
  return {type: ADD_TODO, title, hour}
}
```
