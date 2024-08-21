# Instalação DFIR-IRIS
Neste guia, você aprenderá a instalar o DFIR-IRIS, uma plataforma de gerenciamento de incidentes que integra inteligência artificial para análise primária de alertas. Siga os passos abaixo para configurar o ambiente.

Instalação do DFIR-IRIS
Neste guia, você aprenderá a instalar o DFIR-IRIS, uma plataforma de gerenciamento de incidentes que integra inteligência artificial para análise primária de alertas. Siga os passos abaixo para configurar o ambiente.

Passo a Passo
### 1. Clonando o Repositório
Primeiro, você precisa clonar o repositório do DFIR-IRIS para o diretório /opt:

```
git clone https://github.com/dfir-iris/iris-web.git
```
```
cd iris-web
```
### 2. Configurando a Versão
Para garantir que você está utilizando a versão mais recente e estável do DFIR-IRIS, faça o checkout para a versão disponível mais recente. No exemplo abaixo, estamos usando a versão v2.4.11:

```
git checkout v2.4.11
```
### 3. Configurando o Ambiente
Copie o arquivo de modelo de configuração .env.model para criar o arquivo de configuração .env:

```
cp .env.model .env
```
Edite o arquivo .env conforme necessário para ajustar as configurações do ambiente, como variáveis de ambiente, portas e credenciais.

### 4. Construindo e Inicializando os Contêineres
Agora, construa e inicie os contêineres Docker utilizando docker-compose:
```
docker compose build
docker compose up
```
Os contêineres serão construídos e iniciados, e o DFIR-IRIS estará disponível na sua máquina.

### 5. Acessando o DFIR-IRIS
Após a inicialização, você pode acessar a interface web do DFIR-IRIS no seu navegador. A URL padrão geralmente é https://vm02:443, mas verifique a configuração no arquivo .env se necessário.

Considerações Finais
Certifique-se de que todos os pré-requisitos estão atendidos e que as portas necessárias estão abertas em seu firewall. O DFIR-IRIS deve agora estar funcionando e pronto para ser integrado com outras ferramentas e sistemas de segurança.

Para suporte adicional ou para contribuir com o projeto, consulte a documentação oficial e participe da comunidade no GitHub.
https://github.com/dfir-iris
