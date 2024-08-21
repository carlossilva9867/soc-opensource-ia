# Instalação DFIR-IRIS

cd /opt 
git clone https://github.com/dfir-iris/iris-web.git
cd iris-web


# Faça o checkout para ultima versão disponivel 
git checkout v2.4.11
cp .env.model .env
docker compose build
docker compose up
