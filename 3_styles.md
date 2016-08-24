# 3 Styles

1.Declare Style

```javascript
const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: 'blue',
  },
  text: {
    fontSize: 14,
    color: 'red'
  }
});

```

2.Using Styles

```javascript
class Main extends Component {
  render() {
    return (
      <View style={styles.container}>
        <Text style={styles.text}>I am red.</Text>
      </View>
    );
  }
}
```

3.Properties
 - [View Properties](https://facebook.github.io/react-native/docs/view.html#style)
 - [Image Properties](https://facebook.github.io/react-native/docs/image.html#style)
 - [Text Properties](https://facebook.github.io/react-native/docs/text.html#style)
 - [Flex Properties](https://facebook.github.io/react-native/docs/flexbox.html#content)
 - [Transform Properties](https://facebook.github.io/react-native/docs/transforms.html#content)

