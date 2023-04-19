### Access redis in docker 
1. `docker exec -it **container** bash` <br />
eg: `docker exec -it a49b201f5e9d775c4f70596d242b803fcdf9eb115356e306cf33021687e1cfa7 bash`

2. ENTER `redis-cli` to use the Redis CMD

### Access redis with Django_Redis
1. Get into Django shell
2. from django_redis import get_redis_connection
3. redis = get_redis_connection("default")
4. redis.keys('flow_*')
