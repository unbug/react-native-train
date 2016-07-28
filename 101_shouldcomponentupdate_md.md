# 101_shouldComponentUpdate.md

This chapter can be applied to all react apps.
## shouldComponentUpdate

React is usually fast, but you still can improve performance by optimizing function `[shouldComponentUpdate](https://facebook.github.io/react/docs/component-specs.html#updating-shouldcomponentupdate)`.By default it returns true, if returns false, the render function will be skipped.

This function is frequently invoked when states or props are changed. So it's important to **keep it simple and fast**.
When you called `setState`, the `render` function will always be excuted even if previous states are equal to current. This is where we can make some optimization.

[demo1](https://jsbin.com/figuse/edit?html,js,output)

In demo1, when click button, it will set same state, but render times will still increase.

[demo2](http://jsbin.com/culipes/5/edit?html,js,output)
In demo2, we check the value of name is equal to before or not, if equal return false, then we reduce the times of render function.

But if our states structure is complicated, such as `{ a: { b: c: [1, 2, 3] }}`, we have to compare them deeply. This is obviously against the rules we mentioned above, ** keep shouldComponentUpdate simple**


## Immutable-js
`[Immutable](https://en.wikipedia.org/wiki/Immutable_object)` is a concept from `[functional programming](https://en.wikipedia.org/wiki/Functional_programming)`, one of immutable data features is that it can not be modified after being created. So there are some algorithm to create hash for every data structure(for more [detail](https://en.wikipedia.org/wiki/Persistent_data_structure)).
We can use this feature to prevent deeply compare, shallow compare is enough.
Here we will use [immutable-js](https://facebook.github.io/immutable-js/) from facebook

[demo3](http://jsbin.com/vofubiy/8/edit?html,js,output)
In demo3, we click first button several times, times will only plus one time, click second button , times will increase.
