# PHP Multi version and Nginx
- Para facilitar o desenvolvimento em php utilize esse docker para subir versões 7 e 8 do php ja com suas bibliotecas e compose instalados

## Instação


Primeiro, certifique-se de ter o Docker atualizado.

### Atualize o repositório

bash

```
sudo apt update

```

### Instale os pacotes necessários

bash

```
sudo apt install apt-transport-https ca-certificates curl software-properties-common

```

### Adicione a chave GPG do Docker

bash

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

```

### Adicione o repositório Docker

bash

```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

```

### Instale o Docker Engine

bash

```
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io

```

### Verifique a instalação

bash

```
sudo docker run hello-world

```

### Instale o Docker Compose

bash

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose

```

### Configure o ambiente

Copie o arquivo `.env-exemple` para `.env`:

bash

```
cp .env-exemple .env

```

Edite o arquivo `.env` preenchendo as configurações:

bash

```
PHP_VERSION=7.4

```

## Abordagens para Configuração

ecute o comando para subir os contêineres:

bash

```
docker compose up -d --build

```

Pronto seu docker vai estar disponivel no endereço http://localhost:8080

Utilize os arquivos de configuração nas pastas docker/php e docker/nginx para configurar da melhor forma.