
# Instalação do elastic-stack Docker
 
1) Crie um diretorio e um arquivo em /opt/elk-stack

2) Crie um arquivo chamado docker-compose.yml e adicione o codigo abaixo no arquivo

  ```
version: "3"
services:
  setup:
    image: docker.elastic.co/elasticsearch/elasticsearch:8.12.1
    ports:
    - 9200:9200
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
 3) Crie um arquivo `.env` com as informações de usuario e senha
 ``` 
ELASTIC_PASSWORD=<your-elastic-password>
KIBANA_PASSWORD=<your-kibana-password>
```

Agora você pode subir o container

 ```
 docker compose up -d
```


### Ajuste do Kibana

É necessário ajustar o parâmetro `encryption-keys` no Kibana. Para isso, identifique o ID do contêiner que está rodando o Kibana e gere as chaves de criptografia necessárias.


**Passos para Configuração**

Liste os contêineres para encontrar o ID do contêiner com o nome kibana:
```
docker ps
```
Gere o arquivo de chaves de criptografia:
```
docker exec -it [ID_KIBANA] ./bin/kibana-encryption-keys generate
```
Configure as novas chaves no arquivo de configuração kibana.yml:
```
docker exec -it [ID_KIBANA] /bin/bash -c "echo -e '\nxpack.encryptedSavedObjects.encryptionKey: ecaafedbd4daf82cf92f90d0f7b4fca3\nxpack.reporting.encryptionKey: c2e97cfc7218bb0ff79c63a0be0495de\nxpack.security.encryptionKey: 7e5528384de8ae29cfaf76bb5b928cf2\n' >> config/kibana.yml"
```
**Substitua [ID_KIBANA] pelo ID real do contêiner do Kibana obtido no passo anterior**
