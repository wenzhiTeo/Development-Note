## To access docker db terminal

```
docker-compose exec db sh
psql -U postgres
```

## expose db port for external software (docker-compose.yml)
```
services:
  db:
    ports:
      - "5432:5432"
```

## Postgress analysis tool
https://github.com/dalibo/pev2#all-in-one-local-no-installation-no-network

## Backup DB
```
DB_CONTAINER_NAME=$(docker ps --format "{{.Names}}" | grep 'DB_CONTAINER_NAME')
docker exec $DB_CONTAINER_NAME pg_dumpall -U postgres > backup.sql
```

## Restore DB
```
DB_CONTAINER_NAME=$(docker ps --format "{{.Names}}" | grep 'DB_CONTAINER_NAME')
APP_CONTAINER_NAME=$(docker ps --format "{{.Names}}" | grep 'APP_CONTAINER_NAME')

RESOTRE_FILE=160124_backup.sql

# Copy file into container & run restore
docker cp ./$RESOTRE_FILE $DB_CONTAINER_NAME:/$RESOTRE_FILE
docker exec $DB_CONTAINER_NAME psql -U postgres -f /$RESOTRE_FILE
docker exec $DB_CONTAINER_NAME rm /$RESOTRE_FILE

```
