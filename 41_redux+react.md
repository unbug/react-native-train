# 4.1 Redux

1.Actions & Action Creators

![](QQ20160719-2.png)

```
export const ADD_TODO = 'ADD_TODO';
export function addTodo(title, hour) {
  return {type: types.ADD_TODO, title, hour}
}
```
