# 3.4 Inheritance

1.pass styles as props

```
class InheritanceStyle extends Component {
  render() {
    return (
      <View style={this.props.parentColor}>
      </View>
    );
  }
}

..
...
  <InheritanceStyle parentColor={styles.blue}/>
..
...
```

2.concatenation styles

