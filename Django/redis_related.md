### Access redis in docker 
1. `docker exec -it **container** bash` <br />
eg: `docker exec -it a49b201f5e9d775c4f70596d242b803fcdf9eb115356e306cf33021687e1cfa7 bash`

2. ENTER `redis-cli` to use the Redis CMD

### Access redis with Django_Redis
Get into Django shell

```Python
from django_redis import get_redis_connection
redis = get_redis_connection("default")
redis.keys('flow_*')
for key in x: redis.delete(key)
```
