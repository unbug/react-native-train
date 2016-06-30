# 2.4 Events

1.[`<TouchableHighlight/>`](https://facebook.github.io/react-native/docs/touchablehighlight.html)

```
class Test extends Component {
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
```
class Test extends Component {
  //Does this view want to become responder on the start of a touch?
  handleStartShouldSetResponder(evt){
    return true;
  }
  //Called for every touch move on the View when it is not the responder: does this view want to "claim" touch responsiveness?
  handleMoveShouldSetResponder(evt){
    return true;
  }
  //The View is now responding for touch events. This is the time to highlight and show the user what is happening
  onResponderGrant(evt){
    console.log('you are touching me');
  }
  //Something else is the responder right now and will not release it
  onResponderReject(evt){
    console.log('please wait in line');
  }
  render() {
    return (
      <View 
        onStartShouldSetResponder={this.handleStartShouldSetResponder}
        onMoveShouldSetResponder={this.handleMoveShouldSetResponder}
        onResponderGrant={this.handlePressIn} 
        onResponderReject={this.handlePressOut}>
          <View>
            <Text>Press me!</Text>
          </View>
      </View>
    );
  }
}
```

