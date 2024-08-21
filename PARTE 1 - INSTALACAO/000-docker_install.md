# Instalação do Docker
Siga os passos abaixo para instalar o Docker em sua máquina e verificar se a instalação foi bem-sucedida.

Passo a Passo
### 1. Baixando o Script de Instalação do Docker
Execute o seguinte comando para baixar e executar o script de instalação do Docker:

```
curl -fsSL https://get.docker.com | sh
```
Este comando irá baixar o script de instalação e executá-lo, instalando o Docker na sua máquina.

### 2. Verificando a Instalação
Após a instalação, verifique se o Docker está funcionando corretamente executando o contêiner de teste "hello-world":
```
docker run hello-world
```
Se o Docker estiver instalado e funcionando corretamente, você verá uma mensagem de confirmação indicando que a instalação foi bem-sucedida.