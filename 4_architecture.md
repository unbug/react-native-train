# 4 Architecture

1.[Flux](http://facebook.github.io/flux/docs/overview.html)

![](flux-diagram-white-background.png)
2.Data flow

![](QQ20160719-1.png)

3.Actions & Action Creators

![](QQ20160719-2.png)

```
export function addTodo(title, hour) {
  return {type: types.ADD_TODO, title, hour}
}
```


[Flux TodoMVC Example](https://github.com/facebook/flux/tree/master/examples/flux-todomvc/)

