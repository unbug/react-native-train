# 2.5 View, Text, Image, etc

1. [Core Components](https://facebook.github.io/react-native/docs/tutorial-core-components.html)


```
class Header extends Component {
  render() {
    return (
      <View style={styles.container}>
        <Image
          resizeMode={Image.resizeMode.cover}
          source={require('./img/bg.png')}>
          <Image source={require('../../statics/img/dejaicon.png')}/>
          <Text>
            DEJA
          </Text>
          <Text>
            Find Clothes
          </Text>
          <Text>
            Take a photo of an item and find it!
          </Text>
        </Image>
      </View>
    );
  }
}
```