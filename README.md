# react-redux-persist-sentry-middleware

Redux middleware for sending error reports to Sentry through raven-js.

Will automatically send an error report upon encountering a Javascript error
on dispatching any action. redux-raven-middleware will pass in the error as
well as extra information such as the action that caused the error and the
entire Redux application state.Also, it will add the localStorage data as a
breadcrumb for debugging.

## RavenMiddleware(sentryDSN, sentryConfig, middlewareOptions)

Creates a Raven Middleware.

- `sentryDSN` -- string representing your Sentry instance.
- `sentryConfig` -- object that will be passed into Raven.config.
- `middlewareOptions` -- object to customize the middleware:
 - `actionTransformer` -- transform the action before sending to Sentry
 - `stateTransformer` -- transform the state before sending to Sentry
 - `logger` -- log function to use instead of `console.error`

```js
import {applyMiddleware, createStore} from 'redux';
import RavenMiddleware from 'redux-raven-persist-middleware';


const createStoreWithMiddleware = applyMiddleware(
  RavenMiddleware('my-sentry-dsn')
)(createStore);
```
