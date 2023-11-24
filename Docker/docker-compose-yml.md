``` python
HTTPConnectionPool(host='zipkin', port=9411): Max retries exceeded with url: /api/v2/spans (Caused by NewConnectionError('<urllib3.connection.HTTPConnection object at 0x7f0912fdbd60>: Failed to establish a new connection: [Errno 111] Connection refused'))
```

To fix this we need to set zipkin environment with larger heap size (`JAVA_OPTS=-Xms512m -Xmx1g`)

Example

``` yml
zipkin:
  image: openzipkin/zipkin
  container_name: zipkin
  ports:
    - 9411:9411
  environment:
    - STORAGE_TYPE=elasticsearch
    - ES_HOSTS=elasticsearch:9200
    - JAVA_OPTS=-Xms512m -Xmx1g
  depends_on:
    - elasticsearch
```
