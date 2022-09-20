# Project management client using React and GraphQL client

dependencies:
- @apollo/client
- graphql

## Wrapiing the up into an Appolo client provider:
  
```js
import { ApolloProvider, ApolloClient, InMemoryCache } from '@apollo/client';
```

Cache:
```js
const cache = new InMemoryCache({
  typePolicies: {
    Query: {
      fields: {
        clients: {
          merge(existing, incoming) {
            return incoming;
          },
        },
        projects: {
          merge(existing, incoming) {
            return incoming;
          },
        },
      },
    },
  },
});
```

Appolo client:
```js
const client = new ApolloClient({
  uri: 'http://localhost:5000/graphql',
  cache,
});
```

Wrapping the app in the Appolo provider:
```js
function App() {
  return (
    <>
      <ApolloProvider client={client}>
        <Router>
          ...
        </Router>
      </ApolloProvider>
    </>
  );
}
```


### Create react app

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in your browser.
