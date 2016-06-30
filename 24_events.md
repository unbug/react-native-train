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

```
// Adapted from
// https://github.com/facebook/react-native/blob/master/
// Examples/UIExplorer/PanResponderExample.js
..
...
var CIRCLE_SIZE = 40;
var CIRCLE_COLOR = 'blue';
var CIRCLE_HIGHLIGHT_COLOR = 'green';
var PanResponderExample = React.createClass({
  // Set some initial values.
  _panResponder: {}, 
  _previousLeft: 0, 
  _previousTop: 0, 
  _circleStyles: {}, 
  circle: null,
  getInitialState: function() { 
    return {
          numberActiveTouches: 0,
          moveX: 0,
          moveY: 0,
          x0: 0,
          y0: 0,
          dx: 0,
          dy: 0,
          vx: 0,
          vy: 0,
    } 
  },
  componentWillMount: function() { 
    this._panResponder = PanResponder.create({
      onStartShouldSetPanResponder: this._handleStartShouldSetPanResponder,
      onMoveShouldSetPanResponder: this._handleMoveShouldSetPanResponder, 
      onPanResponderGrant: this._handlePanResponderGrant, 
      onPanResponderMove: this._handlePanResponderMove, 
      onPanResponderRelease: this._handlePanResponderEnd, 
      onPanResponderTerminate: this._handlePanResponderEnd,
    });
    this._previousLeft = 20; 
    this._previousTop = 84; 
    this._circleStyles = {
      left: this._previousLeft,
      top: this._previousTop, 
    };
  },
  componentDidMount: function() { 
    this._updatePosition();
  },
  render: function() { 
    return (
        <View style={styles.container}>
          <View 
          ref={(circle) => { this.circle = circle; }}
          style={styles.circle} {...this._panResponder.panHandlers}/>
          <Text> 
            {this.state.numberActiveTouches} touches, dx: {this.state.dx},
            dy: {this.state.dy},
            vx: {this.state.vx},
            vy: {this.state.vy}
          </Text>
        </View>
    ); 
  },
  // _highlight and _unHighlight get called by PanResponder methods, 
  // providing visual feedback to the user.
  _highlight: function() {
    this.circle && this.circle.setNativeProps({ 
      backgroundColor: CIRCLE_HIGHLIGHT_COLOR
    }); 
  },
  _unHighlight: function() {
    this.circle && this.circle.setNativeProps({
      backgroundColor: CIRCLE_COLOR
    });
  },
  // We're controlling the circle's position directly with setNativeProps.
  _updatePosition: function() {
    this.circle && this.circle.setNativeProps(this._circleStyles);
  },
  _handleStartShouldSetPanResponder: function(e: Object, gestureState: Object): boolean {
    // Should we become active when the user presses down on the circle? 
    return true;
  },
  _handleMoveShouldSetPanResponder: function(e: Object, gestureState: Object): boolean {
    // Should we become active when the user moves a touch over the circle?
    return true; 
  },
  _handlePanResponderGrant: function(e: Object, gestureState: Object) { 
    this._highlight();
  },
  _handlePanResponderMove: function(e: Object, gestureState: Object) { 
    this.setState({
          stateID: gestureState.stateID,
          moveX: gestureState.moveX,
          moveY: gestureState.moveY,
          x0: gestureState.x0,
          y0: gestureState.y0,
          dx: gestureState.dx,
          dy: gestureState.dy,
          vx: gestureState.vx,
          vy: gestureState.vy,
          numberActiveTouches: gestureState.numberActiveTouches
    });
    // Calculate current position using deltas
    this._circleStyles.left = this._previousLeft + gestureState.dx; 
    this._circleStyles.top = this._previousTop + gestureState.dy; 
    this._updatePosition();
  },
  _handlePanResponderEnd: function(e: Object, gestureState: Object) {
    this._unHighlight(); 
    this._previousLeft += gestureState.dx; this._previousTop += gestureState.dy;
  }, 
});
..
...
```