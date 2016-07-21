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
