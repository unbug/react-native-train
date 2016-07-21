# 4.2 [react-redux](https://github.com/reactjs/react-redux)

1.combineReducers()
```
import { combineReducers } from 'redux';
import navigation from './navigation';
import todos from './todos';

const rootReducer = combineReducers({
  navigation, todos
});

export default rootReducer;

```

2.mapStateToProps & mapDispatchToProps

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