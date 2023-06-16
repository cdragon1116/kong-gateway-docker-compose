# kong gateway docker-compose

example docker-compose.yml for kong, postgres and konga.

## Usage

- create network

```
docker network create kong-net
```

- run database

```
docker-compose up kong-database -d
```

- run Kong migration

```
docker-compose up kong-migrations
```

or

```
docker run --rm --network=kong-net \
  -e "KONG_PG_HOST=kong-database" \
  -e "KONG_DATABASE=postgres"         \
  -e "KONG_PG_USER=kong"      \
  -e "KONG_PG_PASSWORD=kongpass"      \
  -e "KONG_PASSWORD=kongpass"         \
 kong:latest kong migrations bootstrap
```

- start up Kong and Konga

```
docker-compose up
```

- verify admin api

```
curl -i http://localhost:8001/
```

- verify gateway

```
curl -i http://localhost:8000/
```

- visit konga on http://localhost:8080
