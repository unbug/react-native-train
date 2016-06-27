# 2.3 Lifecyle

1. Instantiation

 1.1 The lifecycle methods that are called the first time an instance is created
   - getDefaultProps
   - getInitialState
   - componentWillMount
   - render
   - componentDidMount
 
 1.2 For all subsequent uses of that component class:
   - getInitialState
   - componentWillMount
   - render
   - componentDidMount”

2. Lifetime
 - componentWillReceiveProps
 - shouldComponentUpdate
 - componentWillUpdate
 - render
 - componentDidUpdate
 
3. Teardown & cleanup
 - componentWillUnmount