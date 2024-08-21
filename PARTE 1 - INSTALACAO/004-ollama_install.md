
# Instalação ollama
Execute o seguinte comando para baixar e instalar o Ollama:
``` curl -fsSL https://ollama.com/install.sh | sh ```

### Ajustando o Serviço

Após a instalação, ajuste o serviço do Ollama para garantir que ele esteja escutando em todos os endereços IP. Edite o arquivo de configuração do serviço localizado em `/etc/systemd/system/ollama.service` e adicione a linha:
 

    Environment="OLLAMA_HOST=0.0.0.0"

  
Isso garante que o Ollama aceite conexões de qualquer endereço IP.
Recarregando o Serviço 

Após ajustar a configuração, recarregue o serviço e reinicie o Ollama para aplicar as mudanças:

    sudo systemctl daemon-reload
    sudo systemctl restart ollama

  

### Instalação do Open WebUI

Executando o Contêiner Docker

Para instalar e executar o Open WebUI, utilize o seguinte comando Docker. Este comando cria e inicia um contêiner Docker para o Open WebUI:

  

    docker run -d -p 3000:8080 --add-host=host.docker.internal:host-gateway -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main

  
### Instalação do modelo
ollama run [NOME DO MODELO]

