# 2.4 Props & States

1.props: properties are passed to a component and can hold any data
```
class User extends Component {
  render(){
    const user = this.props.data;
    return(
      <View>
        <Text>
          type: {this.props.type}
          Name: {user.name}
          Age: {user.age}
        </Text>
      </View>
    );
  }
}

var user = {name: 'foo', age: 21};
..
...
  <User type="Dev" data={user}/>
..
...
```