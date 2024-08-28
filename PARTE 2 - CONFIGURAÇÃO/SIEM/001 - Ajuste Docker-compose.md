## Configuração do elasticsearchh

Adicione parâmetros de configuração de número de exposição de porta no arquivo `docker-compose` para permitir que o Elasticsearch fique disponível na rede e não somente no localhost na porta 9200. Isso é necessário porque o Shuffle se conecta diretamente com a base de dados do Elasticsearch.

Para realizar esse ajuste, basta adicionar os parâmetros de `ports` no container do Elasticsearch ou baixar o arquivo atualizado deste projeto.

Edite o arquivo `/opt/elk-stack/docker-compose.yml`.  
Adicione as linhas de `ports`:

```yaml
image: docker.elastic.co/elasticsearch/elasticsearch:8.12.1
ports:
  - 9200:9200
```
  
Reinicie o elasticsearch com `docker-compose up -d.`
Verifique se o elasticsearch está rodando na porta 9200 com docker ps.