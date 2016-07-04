# 2 Components
1.MyComponent.js

```
//define component
class MyComponent extends React.Component {
  render() {
    return <Text>My component!</Text>;
  }
}
//export component
export default MyComponent;
```

2.User component

```
import MyComponent from './MyComponent';
..
....
<MyComponent/>
...
..
```
