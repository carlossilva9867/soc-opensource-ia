
# Instalação do Shuffle

1.  **Clonando o Repositório**

    Navegue até o diretório `/opt` e clone o repositório do Shuffle:

    ```    
    cd /opt
    git clone https://github.com/Shuffle/Shuffle
    ```
   
    
    Entre no diretório clonado:
    
    ``` cd Shuffle ``` 
    
2.  **Ajustando Permissões do Diretório**
    
    Crie o diretório para o banco de dados OpenSearch (Elasticsearch) e ajuste as permissões. Isso garante que o Shuffle tenha as permissões adequadas para acessar e gravar no diretório:
        
    `mkdir shuffle-database
    sudo chown -R 1000:1000 shuffle-database` 
    
    O `1000:1000` refere-se ao ID de usuário e grupo que o Docker utiliza por padrão. Ajuste conforme necessário, se você estiver usando IDs diferentes.
    
3.  **Iniciando o Docker Compose**
    
    Inicie os serviços definidos no arquivo `docker-compose.yml` com o comando:

    `docker compose up -d` 
    
    O parâmetro `-d` executa o contêiner em segundo plano (modo daemon), permitindo que o Shuffle seja executado em segundo plano enquanto você realiza outras tarefas.
    
4.  **Verificando o Status**
    
    Após iniciar os serviços, verifique se o Shuffle e os serviços associados estão rodando corretamente:

    
    `docker compose ps` 
    
    Este comando lista os contêineres e seu status, ajudando a confirmar se tudo está funcionando conforme esperado.
    
5.  **Acessando o Shuffle**
    
    Acesse a interface web do Shuffle através do navegador, usando o endereço e a porta configurados no arquivo `docker-compose.yml` (geralmente `http://vm01:3443`, onde `PORTA` é a porta configurada).
    
6.  **Configuração Adicional**
    
    Dependendo da configuração específica do seu ambiente, pode ser necessário realizar ajustes adicionais no arquivo de configuração do Shuffle ou nas configurações do Docker Compose. Consulte a documentação oficial do Shuffle para detalhes sobre configuração e ajustes adiciona