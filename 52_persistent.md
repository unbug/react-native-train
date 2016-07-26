# 5.2 Persistent

1.[AsyncStorage](https://facebook.github.io/react-native/docs/asyncstorage.html)

2.apply [redux-persist](https://github.com/rt2zz/redux-persist) middlewear

```
import { AsyncStorage } from 'react-native';
import { applyMiddleware, createStore, compose } from 'redux';
import thunk from 'redux-thunk';
import {persistStore, autoRehydrate} from 'redux-persist';
import reducers from '../reducers';

var middlewares = compose(applyMiddleware(thunk), autoRehydrate());

export default function configureStore() {
  const store = createStore(reducers, undefined, middlewares);
  persistStore(store, {storage: AsyncStorage});
  return store;
}

```