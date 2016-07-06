# 3.3 Size & Dimensions & onLayout

1.window size

```
let winSize = Dimensions.get('window');
console.log(winSize);

```

2.onLayout

```
class Size extends Component {
  handleTextLayout(evt){
    console.log(evt.nativeEvent.layout);
  }
  render() {
    return (
      <View style={styles.container}>
        <View style={styles.block}/>
        <Text style={styles.text}
          onLayout={this.handleTextLayout}>some text</Text>
      </View>
    );
  }
}
```