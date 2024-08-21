# Instalação Shuffle
cd /opt 
git clone https://github.com/Shuffle/Shuffle
cd Shuffle

# Ajuste de permissões diretório Opensearch database (Elasticsearch):
mkdir shuffle-database   
sudo chown -R 1000:1000 shuffle-database 
docker compose up -d
