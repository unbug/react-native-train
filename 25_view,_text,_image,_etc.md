# 2.5 View, Text, Image, etc

1. [Core Components](https://facebook.github.io/react-native/docs/tutorial-core-components.html)


```
class Header extends Component {
  render() {
    return (
      <View style={styles.container}>
        <Image
          style={styles.bg}
          resizeMode={Image.resizeMode.cover}
          source={require('./img/bg.png')}>
          <Image source={require('../../statics/img/dejaicon.png')}/>
          <Text style={[styles.text, styles.name]}>
            DEJA
          </Text>
          <Text style={[styles.text, styles.title]}>
            Find Clothes
          </Text>
          <Text style={[styles.text, styles.subTitle]}>
            Take a photo of an item and find it!
          </Text>
        </Image>
      </View>
    );
  }
}
```