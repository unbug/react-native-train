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

2.[Gesture Responder System](https://facebook.github.io/react-native/docs/gesture-responder-system.html#responder-lifecycle)

  2.1 Lifecycle
![](QQ20160630-2.png)
 2.2 example
```
class Test extends Component {
  /* Capture handles */
  //the responder system bubbles up from the deepest component, 
  //a parent View wants to prevent the child from becoming responder on a touch start
  handleStartShouldSetResponderCapture(evt){
    return true;
  }
  //the responder system bubbles up from the deepest component, 
  //a parent View wants to prevent the child from becoming responder on a touch move
  handleMoveShouldSetResponderCapture(evt){
    return true;
  }
  
  /* Lifecycle handles */
  //Does this view want to become responder on the start of a touch?
  handleStartShouldSetResponder(evt){
    return true;
  }
  //Called for every touch move on the View when it is not the responder: 
  //does this view want to "claim" touch responsiveness?
  handleMoveShouldSetResponder(evt){
    return true;
  }
  //The View is now responding for touch events. 
  handleResponderGrant(evt){
    console.log('you are touching me');
  }
  //Something else is the responder right now and will not release it
  handleResponderReject(evt){
    console.log('please wait in line');
  }
  
  /* event handles */
  //touch move
  handleResponderMove(evt){
    console.log('touch move at:', 'X='+evt.pageX, 'Y='+evt.pageY);
  }
  //touch end/up
  handleResponderRelease(evt){
    console.log('touch end');
  }
  //Something else wants to become responder. Should this view release the responder?
  handleResponderTerminationRequest(evt){
    return true;
  }
  //touch cancel
  handleResponderTerminate(evt){
    console.log('touch canceled');
  }
  render() {
    return (
      <View 
        onStartShouldSetResponderCapture={this.handleStartShouldSetResponderCapture}
        onMoveShouldSetResponderCapture={this.handleMoveShouldSetResponderCapture}
        onStartShouldSetResponder={this.handleStartShouldSetResponder}
        onMoveShouldSetResponder={this.handleMoveShouldSetResponder}
        onResponderGrant={this.handleResponderGrant} 
        onResponderReject={this.handleResponderReject}
        onResponderMove={this.handleResponderMove}
        onResponderRelease={this.handleResponderRelease}
        onResponderTerminationRequest={this.handleResponderTerminationRequest}
        onResponderTerminate={this.handleResponderTerminate}>
          <Text>Press me!</Text>
      </View>
    );
  }
}
```

2.3 evt is a synthetic touch event with the following form nativeEvent:
 - changedTouches - Array of all touch events that have changed since the last event
 - identifier - The ID of the touch
 - locationX - The X position of the touch, relative to the element
 - locationY - The Y position of the touch, relative to the element
 - pageX - The X position of the touch, relative to the root element
 - pageY - The Y position of the touch, relative to the root element
 - target - The node id of the element receiving the touch event
 - timestamp - A time identifier for the touch, useful for velocity calculation
 - touches - Array of all current touches on the screen

3.[PanResponder](https://facebook.github.io/react-native/docs/panresponder.html)

3.1
```
this._panResponder = PanResponder.create({
  // Ask to be the responder:
  onStartShouldSetPanResponder: (evt, gestureState) => true,
  onStartShouldSetPanResponderCapture: (evt, gestureState) => true,
  onMoveShouldSetPanResponder: (evt, gestureState) => true,
  onMoveShouldSetPanResponderCapture: (evt, gestureState) => true,
  onPanResponderGrant: (evt, gestureState) => {},
  onPanResponderMove: (evt, gestureState) => {},
  onPanResponderTerminationRequest: (evt, gestureState) => true,
  onPanResponderRelease: (evt, gestureState) => {},
  onPanResponderTerminate: (evt, gestureState) => {},
  onShouldBlockNativeResponder: (evt, gestureState) => {},
});
```

3.2 A gestureState object has the following:

 - stateID - ID of the gestureState- persisted as long as there at least one touch on screen
 - moveX - the latest screen coordinates of the recently-moved touch
 - moveY - the latest screen coordinates of the recently-moved touch
 - x0 - the screen coordinates of the responder grant
 - y0 - the screen coordinates of the responder grant
 - dx - accumulated distance of the gesture since the touch started
 - dy - accumulated distance of the gesture since the touch started
 - vx - current velocity of the gesture
 - vy - current velocity of the gesture
 - numberActiveTouches - Number of touches currently on screen


3.3 [PanResponder example in UIExplorer](PanResponder example in UIExplorer)