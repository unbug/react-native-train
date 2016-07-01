# 2.4 Props & States

1.props: properties are passed to a component and can hold any data
```
class User extends Component {
  render(){
    const user = this.props.data;
    this.props.onReady('I am ready!');
    return(
      <View>
        <Text>
          score: {this.props.score}
          type: {this.props.type}
          Name: {user.name}
          Age: {user.age}
        </Text>
      </View>
    );
  }
}
//dufaultProps
User.propTypes = { score: React.PropTypes.number };
User.defaultProps = { score: 0 };

var user = {name: 'foo', age: 21};
class Main extends Component {
  handleReady(str){
    console.log(str);
  }
  render(){
    return(
      <View>
        <User type="Dev" data={user} onReady={this.handleReady}/>
      </View>
    );
  }
}
```
2.state: State differs from props in that it is internal to the component.

```
class Timer extends Component {
  constructor(props) {
    super(props);
    this.state = {count: 0};
  }
  componentDidMount(){
    this.setInterval(this.increase, 1000);
  }
  increase(){
    this.setState({conut: this.state.count+1});
  }
  render(){
    return(
      <View>
        <Text>count: {this.state.count}</Text>
      </View>
    );
  }
}

class Main extends Component {
  render(){
    return(
      <View>
        <Timer/>
      </View>
    );
  }
}
```

3.Changing _props_ and _state_

- | _props_ | _state_ | 
--- | --- | --- 
Can get initial value from parent Component? | Yes | Yes
Can be changed by parent Component? | Yes | No
Can set default values inside Component?* | Yes | Yes
Can change inside Component? | No | Yes
Can set initial value for child Components? | Yes | Yes
Can change in child Components? | Yes | No

\* Note that both _props_ and _state_ initial values received from parents override default values defined inside a Component.

4._props_ VS _state_
 - Use props to pass data and settings through the component tree.
 - Never modify this.props or call this.setprops inside of a component; consider props immutable.
 - Use props to for event handlers to communicate with child components.
 - Use state for storing simple view state like wether or not drop-down options are visible.
 - Never modify this.state directly, use this.setstate instead.