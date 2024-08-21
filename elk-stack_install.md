# Docker-compose
```
version: "3"
services:
  setup:
    image: docker.elastic.co/elasticsearch/elasticsearch:8.12.1
    environment:
      - ELASTIC_PASSWORD=${ELASTIC_PASSWORD}
      - KIBANA_PASSWORD=${KIBANA_PASSWORD}
    container_name: setup
    command:
      - bash
      - -c
      - |
        echo "Waiting for Elasticsearch availability";
        until curl -s http://elasticsearch:9200 | grep -q "missing authentication credentials"; do sleep 30; done;
        echo "Setting kibana_system password";
        until curl -s -X POST -u "elastic:${ELASTIC_PASSWORD}" -H "Content-Type: application/json" http://elasticsearch:9200/_security/user/kibana_system/_password -d "{\"password\":\"${KIBANA_PASSWORD}\"}" | grep -q "^{}"; do sleep 10; done;
        echo "All done!";

  elasticsearch:
    image: docker.elastic.co/elasticsearch/elasticsearch:8.12.1
    # give the container a name
    # this will also set the container's hostname as elasticsearch
    container_name: elasticsearch
    environment:
      - discovery.type=single-node
      - cluster.name=elasticsearch
      - bootstrap.memory_lock=true
      # limits elasticsearch to 1 GB of RAM
      - ES_JAVA_OPTS=-Xms1g -Xmx1g
      # The password for the 'elastic' user
      - ELASTIC_PASSWORD=${ELASTIC_PASSWORD}
      - xpack.security.http.ssl.enabled=false

  kibana:
    image: docker.elastic.co/kibana/kibana:8.12.1
    container_name: kibana
    ports:
      - 5601:5601
    environment:
      # remember the container_name for elasticsearch?
      # we use it here to access that container
      - ELASTICSEARCH_HOSTS=http://elasticsearch:9200
      - ELASTICSEARCH_USERNAME=kibana_system
      - ELASTICSEARCH_PASSWORD=${KIBANA_PASSWORD}
      # Change this to true if you want to sent
      # telemetry data to kibana developers
      - TELEMETRY_ENABLED=false
```
