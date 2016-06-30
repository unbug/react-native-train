# 2.5 View, Text, Image, etc

1. [Core Components](https://facebook.github.io/react-native/docs/tutorial-core-components.html)


```
..
...
render() {
  return (
    <View>
      <Text>This is a list!</Text>
      <ListView>
        <View>
          <Text>This is a text!</Text>
          <Image source={require('./img/check.png')} />
        </View>
        <View>
          <Text>This is a text!</Text>
          <Image source={require('./img/check.png')} />
        </View>
        <View>
          <Text>This is a text!</Text>
          <Image source={require('./img/check.png')} />
        </View>
        <View>
          <Text>This is a text!</Text>
          <Image source={require('./img/check.png')} />
        </View>
      </ListView>
    </View>
  );
}
..
...
```