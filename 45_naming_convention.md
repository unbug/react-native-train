# 4.5 Naming convention

1.Containers & Components

1.1 Container file: ```src/containers/ModuleNameView.js```, Component files:```src/components/module-name-view```
```
module-name-view
 - index.js
 - Main.js
 - Header.js
 - ...
 - img
   - icon@2x.png
   - icon@3x.png
```

1.2 Event name: 

```
handleEventName = ()=>{//todo}
...
<MyComponent onEventName={this.handleEventName}/>
```

1.3 Render methods:

```
  renderMethodName = () => {
   //todo
  }
  render() {
    return (
      <View>
        {this.renderMethodName()}
      </View>
    );
  }
````
1.4mapStateToProps & mapDispatchToProps

```
```
function mapStateToProps(state) {
  return {
    todos: state.todos
  };
}

function mapDispatchToProps(dispatch) {
  return {
    actions: bindActionCreators(Actions, dispatch)
  }
}
```
```

2.actions

2.1```src/constants/ActionTypes.js```

````
export const SWITCH_MAIN_TAB = 'SWITCH_MAIN_TAB';

````
2.2```src/actions/todos.js````
```

```
import * as types from '../constants/ActionTypes'

export function addTodo(title, hour) {
  return {type: types.ADD_TODO, title, hour}
}
```