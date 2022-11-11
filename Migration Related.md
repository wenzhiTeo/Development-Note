## Update permission to save the file
`sudo chown -R *user* agent_status/`

## Access the postgres DB
`sudo docker-compose exec db psql -U postgres`


## Fix chown error

open cmd -> `wsl -d Ubuntu-22.04 -u root`


`chown root:root /etc/*`
