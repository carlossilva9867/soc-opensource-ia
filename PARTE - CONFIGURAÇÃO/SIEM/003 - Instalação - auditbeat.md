
**Download do auditbeat:**

Acesse a página de download do elasticsearch: https://www.elastic.co/downloads/elasticsearch.
Baixe o pacote .deb do auditbeat para a versão 8.12.1
Copie o arquivo para o servidor Linux via SSH.

Ou baixe direto no servidor com comando
´
`wget https://artifacts.elastic.co/downloads/beats/auditbeat/auditbeat-8.12.1-amd64.deb`

### Instalação do auditbeat:

Instale o auditbeat com o comando: `sudo dpkg -i auditbeat-8.12.1-amd64.deb`
Configuração do auditbeat:

Edite o arquivo `/etc/auditbeat/auditbeat.yml`.
Altere o parâmetro os parametros abaixo

    output.elasticsearch.hosts     (IP do servidor do elasticsearch)
    output.elasticsearch.username  (Usuario elasticsearhc)
    output.elasticsearch.password  (senha)  

---

## Configure as regras de auditoria no parâmetro auditd.log.
Teste de comunicação:
Execute o comando `sudo auditbeat test output para` testar a comunicação com o elasticsearch.\
Início do serviço:

Inicie o serviço auditbeat com o comando `sudo systemctl start auditbeat`.
Verifique o status do serviço com o comando `sudo systemctl status auditbeat`.

---

### Verificação dos logs no Kibana
Acesse o Kibana:

Abra o navegador e acesse `http://ip_do_elk-stack:5601.`
Crie um novo dataview para o índice auditbeat.
Selecione o timestamp @timestamp como campo de tempo.
Visualização dos logs:

Os logs do auditbeat serão exibidos no Kibana.
Você pode filtrar e analisar os logs para identificar anomalias e atividades suspeitas.
Observações

Para mais informações, consulte a documentação do elasticsearch e do auditbeat.
Links úteis
Documentação do elasticsearch: https://www.elastic.co/docs\
Documentação do auditbeat: https://www.elastic.co/guide/en/beats/auditbeat/current/auditbeat-overview.html


Video mostrando o processo de instalação e configuração do beats
[![Formas de envio de log](https://img.youtube.com/vi/LfXCBtRyodM/maxresdefault.jpg)](https://www.youtube.com/watch?v=LfXCBtRyodM)
