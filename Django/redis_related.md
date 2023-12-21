### Access redis in docker 
1. `docker exec -it **container** bash` <br />
eg: `docker exec -it a49b201f5e9d775c4f70596d242b803fcdf9eb115356e306cf33021687e1cfa7 bash`

2. ENTER `redis-cli` to use the Redis CMD
3. View available db `info keyspace`
Example result
```console 
127.0.0.1:6379> info keyspace
# Keyspace
db0:keys=950,expires=949,avg_ttl=10098008
db1:keys=615,expires=1,avg_ttl=253643
```

4. Select db `select 1`
Example result
```console 
127.0.0.1:6379> select 1
OK
127.0.0.1:6379[1]> keys *
```

### Access redis with Django_Redis
Get into Django shell

```Python
from django_redis import get_redis_connection
redis = get_redis_connection("default")
redis.keys('flow_*')
for key in x: redis.delete(key)
```
