## 使用Docker部署Postgres11+Timescaledb

docker-compose.yml

```yml
version: '3'
services:
  pg:
    image: "pg:v11"
    environment: # docker run -e
      - POSTGRES_PASSWORD=jack5209
    build:
      context: .
      dockerfile: Dockerfile
      args: # --build-arg
        PREV_TS_VERSION: 1.3.2
        PG_VERSION: 11
    ports:
      - "5432:5432"
    container_name: "pg11"
    volumes:
      - /var/lib/postgresql/data:/var/lib/postgresql/data
```

Reference:

- [timescaledb-docker](https://github.com/timescale/timescaledb-docker)
- [docker-library/postgres](https://github.com/docker-library/postgres/blob/0d0485cb02e526f5a240b7740b46c35404aaf13f/11/alpine/Dockerfile)
