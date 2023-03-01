# related docker command
docker-compose -f docker-compose.test.yml up -d --build <br />
docker-compose -f docker-compose.test.yml run web bash run_test.sh <br />

# run specific test
pipenv run python manage.py shell  <br />
pipenv run pytest -k "test..." --reuse-db  <br />

# run forever 
while true; do **pipenv run python manage.py test -----** ; done

# run 5 times
for i in {1..5}; do **pipenv run python manage.py test -----** ; done

# Testcases related to Redis
Django wont reset/flush the Redis, sometimes this behaviour might lead test fail

```Python
import fakeredis
from django.core.cache import cache
from unittest.mock import patch

from api.tests.graphql import GraphQLTestCase

class xxxTestCase(GraphQLTestCase):
    def setUp(self):
        super().setUp()
        self.loaders_get_redis_connection_patcher = patch(
            "your_module.loaders.get_redis_connection", fakeredis.FakeStrictRedis
        )
        self.utils_get_redis_connection_patcher = patch(
            "your_module.utils.get_redis_connection", fakeredis.FakeStrictRedis
        )
        self.loaders_get_redis_connection_patcher.start()
        self.utils_get_redis_connection_patcher.start()

    def tearDown(self):
        super().tearDown()
        self.loaders_get_redis_connection_patcher.stop()
```
