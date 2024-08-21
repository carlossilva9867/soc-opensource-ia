# Instalação ollama
curl -fsSL https://ollama.com/install.sh | sh

# Ajuste do serviço /etc/systemd/system/ollama.service
Environment="OLLAMA_HOST=0.0.0.0"

# Instalação Open WebUI 
docker run -d -p 3000:8080 --add-host=host.docker.internal:host-gateway -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main
