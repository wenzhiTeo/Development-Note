# show the cache status

## First Way
```
  console.log(__APOLLO_CLIENT__.cache.data);
```

## Second Way
```  
  const client = useApolloClient();
  console.log(client.cache);
```
