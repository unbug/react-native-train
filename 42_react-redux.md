# 4.2 [react-redux](https://github.com/reactjs/react-redux)
1.Actions

```
import * as  navigationActions from './navigation';
import * as  todosActions from './todos';

export default {...navigationActions, ...todosActions};
```

2.combineReducers()
```
import { combineReducers } from 'redux';
import navigation from './navigation';
import todos from './todos';

const rootReducer = combineReducers({
  navigation, todos
});

export default rootReducer;

```

3.mapStateToProps & mapDispatchToProps

```
import { bindActionCreators } from 'redux';
import { connect } from 'react-redux';
...

...
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

export default connect(
  mapStateToProps,
  mapDispatchToProps
)(TodoView);
```