# 2.4 Events

1.[`<TouchableHighlight/>`](https://facebook.github.io/react-native/docs/touchablehighlight.html)

```
class Header extends Component {
  handlePress(){
    console.log('press');
  }
  handleLongPress(){
    console.log('longPress');
  }
  handlePressIn(){
    console.log('pressIn');
  }
  handlePressOut(){
    console.log('pressIn');
  }
  render() {
    return (
      <TouchableHighlight 
        onPress={this.handlePress}
        onLongPress={this.handleLongPress}
        onPressIn={this.handlePressIn} 
        onPressOut={this.handlePressOut}>
          <View>
            <Text>Press me!</Text>
          </View>
      </TouchableHighlight>
    );
  }
}
```

2.[GestureResponder System Lifecycle](https://facebook.github.io/react-native/docs/gesture-responder-system.html#responder-lifecycle)




![](QQ20160630-2.png)
