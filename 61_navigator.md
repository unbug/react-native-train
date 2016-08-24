# 6.1 Navigator

1.define routes

```javascript

import MainTabsView from './MainTabsView';
import EditView from './EditView';
import BroswerView from './BroswerView';

const ROUTES = { MainTabsView,  BroswerView, EditView };
```

2.config Navigator

```javascript
class App extends Component {
  renderScene = (route, navigator) => {
    let Scene = ROUTES[route.name];
    return <Scene {...route} navigator={navigator}/>;
  }
  configureScene = (route, routeStack) => {
    switch (route.name){
      case 'EditView':
        return Navigator.SceneConfigs.FloatFromBottom;
      default:
        return Navigator.SceneConfigs.PushFromRight;
    }
  }
  render() {
    return (
      <View style={styles.container}>
        <StatusBar barStyle="light-content"/>
        <Navigator
          initialRoute={{name: 'MainTabsView'}}
          renderScene={this.renderScene}
          configureScene={this.configureScene}/>
      </View>
    )
  }
}
```

3.forward & back

![](QQ20160727-2.png)



```javascript
...
  handleEdit = ()=>{
    //Navigate forward to a new scene
    this.props.navigator.push({name: 'EditView', data: this.props.data});
  }
...
```

```javascript
...
  close = ()=>{
    //Transition back and unmount the current scene
    this.props.navigator.pop();
  }
...
```
![](QQ20160727-1.png)


4.onDidFocus & onWillFocus

```javascript
...
componentDidMount(){
    this.currentRoute = this.props.navigator.navigationContext.currentRoute;
    this.bindEvents();
  }
  componentWillUnmount(){
    this.unBindEvents();
  }
  bindEvents = ()=>{
    this.willFocusSubscription  = this.props.navigator.navigationContext.addListener('willfocus', (event) => {
      if (this.currentRoute !== event.data.route) {
        this.setState({isVisible: false});
      }
    });
    this.didFocusSubscription  = this.props.navigator.navigationContext.addListener('didfocus', (event) => {
      if (this.currentRoute === event.data.route) {
        this.setState({isVisible: true});
      }
    });
  }
  unBindEvents = ()=>{
    this.willFocusSubscription.remove();
    this.didFocusSubscription.remove();
  }
...
```