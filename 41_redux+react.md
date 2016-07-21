# 4.1 Redux

1.[Actions](https://github.com/acdlite/flux-standard-action) & Action Creators

```
//action type
const ADD_TODO = 'ADD_TODO';

//action creator, semantic methods that create actions
//collected together in a module to become an API
function addTodoAction(title, hour) {
  //action, an object with a type property and new data, like events
  return {type: ADD_TODO, title, hour}
}
```
2.[Reducers](http://redux.js.org/docs/basics/Reducers.html)

```
//a function that accepts an accumulation and a value and returns a new accumulation.
function todoReducers(state = [], action) {
  switch (action.type) {
    case ADD_TODO:
      //always create new state, never mutate old state
      return [
        {
          id: Utils.GUID(),
          title: action.title,
          endTime: getEndTime(action.hour),
          completed: false
        },
        ...state
      ]
    default:
      //return default state
      return state
  }
}

```
3.Store

```
import { createStore } from 'redux';
//define store
let store = createStore(todoReducers);

class TodoView extends Component {
  constructor(props){
    super(props);
    this.state = {todos: []};
  }
  componentDidMount(){
    //subscribe store
    this.unsubscribeStore = store.subscribe(() =>
      this.setState({todos: store.getState()});
    );
  }
  componentWillUnmount(){
    //unsubscribe store
    this.unsubscribeStore();
  }
  renderTodoList = ()=>{
    //reder todo list
    return this.state.todos.map( (todo)=> {
      return <Text key={todo.id}>Todo: {todo.title}</Text>
    });
  }
  handleAddTodo = (num)=>{
    //dispatching actions
    store.dispatch( addTodoAction(`Create a new todo ${num}`) );
  }
  render() {
    return (
      <View>
        <TouchableHighlight onPress={this.handleAddTodo}>
          <Text>Add Todo</Text>
        </TouchableHighlight>
        <ScrollView>{this.renderTodoList(Math.random())}</ScrollView>
      </View>
    );
  }
}

```
4.C