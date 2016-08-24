# 2 Components
1.MyComponent.js

```javascript
//define component
class MyComponent extends React.Component {
  render() {
    return <Text>My component!</Text>;
  }
}
//export component
export default MyComponent;
```

2.Main.js

```javascript
//import component
import MyComponent from './MyComponent';
class Main extends React.Component {
  render() {
    //use component
    return <MyComponent>;
  }
}
```
3.AppRegistry

```javascript
AppRegistry.registerComponent('MyApp', () => Main);
```
