# 4.1 [Redux](http://redux.js.org/)

1.Actions & Action Creators

![](QQ20160719-2.png)

```
const ADD_TODO = 'ADD_TODO';
function addTodo(title, hour) {
  return {type: ADD_TODO, title, hour}
}
```
