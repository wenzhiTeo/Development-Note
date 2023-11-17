## Elasticsearch Default Size is 10
https://www.elastic.co/guide/en/elasticsearch/reference/8.1/paginate-search-results.html

## ESTestCase is useful term to trigger the Setup & Teardown Operation
https://github.com/django-es/django-elasticsearch-dsl/blob/master/django_elasticsearch_dsl/test/testcases.py#L15

## Error fixing
`'Validation Failed: 1: this action would add [2] total shards, but this cluster currently has [1000]/[1000] maximum shards open;'`
```
curl -X PUT localhost:9200/_cluster/settings -H "Content-Type: application/json" -d '{ "persistent": { "cluster.max_shards_per_node": "2500" } }'
```
