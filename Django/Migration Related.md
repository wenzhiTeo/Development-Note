## Update permission to save the file
`sudo chown -R *user* agent_status/`

## Access the postgres DB
`sudo docker-compose exec db psql -U postgres`

## Check migration status
`pipenv run python manage.py showmigrations | grep '\[ \]'`


