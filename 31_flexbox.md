 # 3.1 Flexbox


1.[Flexbox layout](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
  >The main idea behind the flex layout is to give the container the ability to alter its items' width/height (and order) to best fill the available space (mostly to accommodate to all kind of display devices and screen sizes). A flex container expands items to fill available free space, or shrinks them to prevent overflow.


![](QQ20160705-15.png)


2.flex:1

![](QQ20160705-2.png)

 ```javascript
const styles = StyleSheet.create({
  container: {
    flex: 1
  },
  header: {
    height: 200,
    backgroundColor: 'red'
  },
  main: {
    flex: 1,
    backgroundColor: 'blue'
  },
  footer: {
    height: 200,
    backgroundColor: 'green'
  },
  text: {
    color: '#ffffff',
    fontSize: 80
  }
});
 ```
3.flexDirection:'row'|'column'

![](QQ20160705-7.png)

![](QQ20160705-8.png)


4.justifyContent:'flex-start'|'flex-end'|'center'|'space-between'|'space-around'

![](QQ20160705-10.png)

5.alignItems:'flex-start'|'flex-end'|'center'|'stretch'

![](QQ20160705-12.png)

6.alignSelf:'auto'|'flex-start'|'flex-end'|'center'|'stretch'

![](QQ20160705-13.png)

7.flexWrap:'wrap'|'nowrap'

![](QQ20160705-14.png)

8.Box model

![](QQ20160705-16.png)

width = borderLeftWidth(25)+paddingLeft(25)+100+borderRightWidth(25)+paddingRight(25)=200

height = borderTopWidth(25)+paddingTop(25)+100+borderBottomWidth(25)+paddingBottom(25)=200
```javascript
class Main extends Component {
  render() {
    return (
      <View style={styles.container}>
        <View style={styles.header}>
          <Text style={styles.text}>200X100</Text>
        </View>
        <View style={styles.main}>
          <View  style={styles.mainContent}>
            <Text style={styles.text}>100X100</Text>
          </View>
        </View>
        <View style={styles.footer}>
          <Text style={styles.text}>200X100</Text>
        </View>
      </View>
    );
  }
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center'
  },
  header: {
    height: 100,
    width: 200,
    backgroundColor: 'red'
  },
  main: {
    height: 200,
    width: 200,
    padding: 25,
    borderWidth: 25,
    borderColor: 'black',
    margin: 25,
    backgroundColor: 'blue'
  },
  mainContent: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: 'red'
  },
  footer: {
    height: 100,
    width: 200,
    backgroundColor: 'green'
  },
  text: {
    color: '#ffffff',
    fontSize: 20
  }
});
```

![](QQ20160705-17.png)



