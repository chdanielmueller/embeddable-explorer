# Apollo Studio Embeddable Explorer

This repo hosts the source for Apollo Studio's Embeddable Explorer

[See docs for usage details](https://www.apollographql.com/docs/studio/embed-explorer/)

### Using the [@apollo/explorer npm package](https://www.npmjs.com/package/@apollo/explorer)

You can download the @apollo/explorer npm package with `npm install @apollo/explorer`. Then, you can import the EmbeddedExplorer class like so:

```
import EmbeddedExplorer from '@apollo/explorer';
```

When you call the EmbeddedExplorer constructor with a `target` of an html div you have in your app, the Explorer will show up in an iframe in that element. Check out all the [configuration options](https://www.apollographql.com/docs/studio/explorer/embed-explorer/#options) for your graph.

```
function App() {

  useEffect(() => {
    new EmbeddedExplorer({
      target: '#embeddableExplorer',
      graphRef: 'acephei@current',
      endpointUrl: 'https://acephei-gateway.herokuapp.com',
      initialState: {
        document: `query Example {
me {
  id
}
}`,
        variables: {
          test: 'abcxyz',
        },
        displayOptions: {
          showHeadersAndEnvVars: true,
        },
      },
    });
  })
  
  return (
    <div
      style={{width: '800px', height: '700px', margin: 'auto'}}
      id="embeddableExplorer"
    />
  );
}
```

### Examples from the raw cdn hosted umd file

- [Embedding a registered public graph](./src/examples/graphRef.html)
- [Usage by directly passing in schema](./src/examples/manualSchema.html)
