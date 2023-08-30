To access docker db terminal

```
docker-compose exec db sh
psql -U postgres
```

expose db port for external software (docker-compose.yml)
```
services:
  db:
    ports:
      - "5432:5432"
```

Postgress analysis tool
https://github.com/dalibo/pev2#all-in-one-local-no-installation-no-network
