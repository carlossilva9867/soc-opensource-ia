
1.  **Download do Winlog Beat:**
    
    -   Acesse o site oficial da Elastic e baixe a versão mais recente do Winlog Beat compatível com seu sistema operacional:  [Winlogbeat 8.12.1](https://artifacts.elastic.co/downloads/beats/winlogbeat/winlogbeat-8.12.1-windows-x86_64.zip)
    -   Extraia o arquivo ZIP para um diretório de sua preferência.
2.  **Configuração do Winlog Beat:**
    -   **Arquivo de configuração:** Abra o arquivo `winlogbeat.yml` no diretório extraído.
    -   **Output:** Configure a saída para o ElasticSearch, especificando o endereço IP ou nome de host, porta, usuário e senha.
        ```
        output.elasticsearch:
          hosts: ["http://seu_elasticsearch_host:9200"]
          username: "elastic"
          password: "changeme"
        ```
        
3.  **Execução do Winlog Beat:**
    
    -   **Em primeiro plano:** Execute o comando `winlogbeat.exe -e` para executar o Winlog Beat em primeiro plano.
    -   **Como serviço:** Instale o Winlog Beat como um serviço do Windows para que ele seja iniciado automaticamente. Basta executar esse script no diretorio que foi descompactado
        
        ```
        .\install-service-winlogbeat.ps1  
        ```
		 Caso o Windows bloqueie a execução do PowerShell na máquina, rode o comando abaixo como administrador.
			 ```
			Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Scope CurrentUser
			 ```
        
4.  **Verificação da instalação:**
    -   Verifique se o Winlog Beat está em execução e enviando dados para o ElasticSearch.
    -   Use o Kibana para visualizar os dados coletados.

### Documentação Oficial
Para obter informações mais detalhadas e atualizadas sobre o Winlog Beat, consulte a documentação oficial da Elastic:  [https://www.elastic.co/guide/en/beats/winlogbeat/current/index.html](https://www.elastic.co/guide/en/beats/winlogbeat/current/index.html)

Video mostrando o processo de instalação e configuração do beats
[![Formas de envio de log](https://img.youtube.com/vi/EkfA8_D7GKc/maxresdefault.jpg)](https://www.youtube.com/watch?v=EkfA8_D7GKc)