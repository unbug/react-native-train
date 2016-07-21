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
3.configureStore()

```
import { createStore } from 'redux';
import reducers from '../reducers';

export default function configureStore() {
  const store = createStore(reducers, undefined);
  return store;
}

```

4.Provider

```
import React, { Component } from 'react';
import { Provider } from 'react-redux';

import App from './containers/App';
import configureStore from './store/configureStore';

class Root extends Component {
  render() {
    return (
      <Provider store={configureStore()}>
        <App />
      </Provider>
    );
  }
}

export default Root;
```
3.mapStateToProps & mapDispatchToProps

```
import { bindActionCreators } from 'redux';
import { connect } from 'react-redux';

class App extends Component {
  constructor(props){
    super(props);
    this.state = {todos: []};
  }
  componentDidMount(){
    //2. subscribe store
    this.unsubscribeStore = store.subscribe(() =>{
      //3. getState
      this.setState({todos: store.getState()});
    });
  }
  componentWillUnmount(){
    //5. unsubscribe store
    this.unsubscribeStore();
  }
  renderTodoList = ()=>{
    //reder todo list
    return this.state.todos.map( (todo)=> {
      return <Text key={todo.id}>Todo: {todo.title}</Text>
    });
  }
  handleAddTodo = ()=>{
    //4. dispatching actions
    store.dispatch( addTodoAction('Create a new todo', 8) );
  }
  render() {
    return (
      <View>
        <TouchableHighlight onPress={this.handleAddTodo}>
          <Text>Add Todo</Text>
        </TouchableHighlight>
        <ScrollView>{this.renderTodoList()}</ScrollView>
      </View>
    );
  }
}

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