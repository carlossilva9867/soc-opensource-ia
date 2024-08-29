Este é o objeto principal do nosso workflow, que contém a query a ser utilizada para capturar os alertas do índice no Elasticsearch. Se você estiver na versão 8, pode utilizar os mesmos valores que eu utilizei ou personalizar de acordo com suas necessidades. Abaixo estão as configurações que eu utilizei no projeto.

**Observação**: Certifique-se de que o body atende às suas necessidades e que o índice existe no Elasticsearch.

![Node_ELK](https://github.com/carlossilva9867/soc-opensource-ia/blob/main/IMG/node_elk_shuffle.png?raw=true)


**Nome do objeto**: GET_ALERTS\
**Index**: .alerts-security.alerts-default

Body
```
{
  "_source": {
    "includes": [
      "@timestamp",
      "kibana.alert.rule.name",
      "kibana.alert.reason",
      "event.category",
      "host.hostname",
      "kibana.alert.status",
      "kibana.alert.rule.description",
      "event.code"
    ]
  },
  "size": 200,
  "query": {
    "bool": {
      "filter": [
        {
          "range": {
            "@timestamp": {
              "gte": "now-30m",
              "lt": "now/m"
            }
          }
        },
        {
          "term": {
            "kibana.alert.workflow_status": "open"
          }
        }
      ]
    }
  }
}
``` 

Video mostrando o processo de configuração no shuffle
[![SHUFFLE COM ELASTIC](https://img.youtube.com/vi/LfXCBtRyodM/maxresdefault.jpg)](https://youtu.be/_pajqTdyLkU)