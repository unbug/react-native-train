# 101_shouldComponentUpdate.md

This chapter can be applied to all react apps.
React is usually fast, but you still can improve performance by optimizing function `shouldComponentUpdate`

This function is frequently invoked when states or props are changed. So it's important to **keep it simple and fast**.
When you called `setState`, the `render` function will always be excuted even if previous states are equal to current. This is where we can make some optimization.

demo1

In demo1, when clicking button, it will set same state, but render times will still increase.


