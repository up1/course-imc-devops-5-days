# Start PostgreSQL server and PgAdmin tool

```
$docker-compose up -d
$docker-compose ps

      Name                     Command              State               Ports
-----------------------------------------------------------------------------------------
pgadmin_container   /entrypoint.sh                  Up      443/tcp, 0.0.0.0:5050->80/tcp
postgres            docker-entrypoint.sh postgres   Up      0.0.0.0:5432->5432/tcp
```

## Access to PgAdmin:
* URL: http://server-ip:5050
* Username: `pgadmin4@pgadmin.org` (as a default)
* Password: `admin` (as a default)

## Access to postgres:
* server-ip:5432
* Username: `postgres` (as a default)
* Password: `changeme` (as a default)

## Add a new server in PgAdmin
* Host name/address `postgres`
* Port 5432
* Username as POSTGRES_USER, by default: `postgres`
* Password as POSTGRES_PASSWORD, by default `changeme`

## Create tables and insert data for testing
* Copy data from file `data.sql` to PgAdmin