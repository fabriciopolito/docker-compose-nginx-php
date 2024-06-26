
# Docker Compose PHP e Nginx

## Esta stack consiste nos seguintes pacotes e configurações:

- **Nginx**
- **PHP-FPM** 7 ou 8 (incluindo Git, curl, Xdebug e Composer)

### Instalação

- Clonar este repositório.
- Caso desejado, alterar o arquivo de configurações no `./.env`
- Caso desejado, alterar os arquivos de configurações em `./etc/`
- Coloque seus arquivos fonte em `./public/`
- Por fim, execute: `docker compose up -d`

### Listar os containers em execução

- `docker container ls`

### Parar um container específico

- `docker container stop <nome_ou_id>`

### Reiniciar um container específico

- `docker container restart <nome_ou_id>`

### Derrubar todos os contêineres desta stack

- `docker compose down`

### Acessar o terminal do Nginx

- `docker container exec -it nginx_server sh` ou `docker container exec -it <nome_do_servico_no_docker_compose-ou-id> sh`

Teste de comunicação entre os dois container, no terminal do Nginx: 
- `ping php_service`

### Acessar o terminal do PHP

- `docker container exec -it php-fpm_server bash` ou `docker container exec -it <nome_do_servico_no_docker_compose-ou-id> bash`

Teste de comunicação entre os dois container, no terminal do PHP: 

- `ping nginx_server`

### Inspecionar os contêineres

- `docker container inspect nginx_server`
- `docker container inspect php-fpm_server`

### Ver o consumo dos recursos

- `docker container stats`

- `ctrl + c` para sair.

### Limpar os caches do Docker

- Visualizando espaço utilizado pelo Docker: `docker system df`
- Removendo contêineres do cache: `docker container prune -f`
- Removendo imagens do cache não vinculado a contêineres: `docker image prune -f` 
- Removendo volumes anônimos: `docker volume prune -f`
- Removendo cache de compilação: `docker buildx prune -f`
- Removendo rede não utilizadas: `docker network prune -f`
- **Removendo tudo**: `docker system prune --volumes -af`

### Personalizar

Você é livre para adicionar quaisquer outras imagens a esta stack, como:

- Banco de Dados (por exemplo, MySQL, PostgreSQL, Redis)
- phpMyAdmin
- Mensageria (por exemplo, RabbitMQ, Kafka)

Basta incluir as configurações correspondentes no arquivo `docker-compose.yml`.
