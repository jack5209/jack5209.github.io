## 使用Docker部署elasticsearch

docker-compose.yml

```yml
version: '3'
services:
  es01:
    image: es:v7
    container_name: es01
    environment:
      - node.name=es01
      - cluster.name=es-docker-cluster
      - network.host=0.0.0.0
      # - discovery.seed_hosts=es02,es03
      - cluster.initial_master_nodes=es01
      # - cluster.initial_master_nodes=es01,es02,es03
      - bootstrap.memory_lock=true
      - "ES_JAVA_OPTS=-Xms2g -Xmx2g" # set the heap size to use 2GB
    ulimits:
      nproc: 4096 # max number of threads,not below 4096
      nofile:
        soft: 65536
        hard: 65536
      memlock:
        soft: -1
        hard: -1
    deploy:
      resources:
        limits:
          memory: 3g
    volumes:
      - /elasticsearch/data:/usr/share/elasticsearch/data
    ports:
      - 9200:9200
```

[github](https://github.com/jack5209/dockerfiles/tree/7.5/elasticsearch)

Reference:

- [docker-elasticsearch](https://github.com/elastic/dockerfiles/tree/7.5/elasticsearch)

- [Install Elasticsearch with Docker](https://www.elastic.co/guide/en/elasticsearch/reference/7.5/docker.html)
