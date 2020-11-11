# Ambiente Laravel para Docker

## 💻 Ambiente

Ambiente completo de desenvolvimento Laravel.

- [x] NGINX
- [x] PHP 7
- [x] MySQL 5
- [x] phpMyAdmin
- [x] Composer

## 🚀 Execução

### Pré-requisitos:

- Docker e Docker Compose.
- Não ter nenhuma aplicação executando nas portas 8080, 8081, 3306 e 9000.

### Instalação do Docker e Docker Compose:

- <a href="https://docs.docker.com/engine/install/" target="_blank">Instalação do Docker</a>
- <a href="https://docs.docker.com/compose/install/" target="_blank">Instalação do Docker Compose</a>

No Ubuntu:
```bash
# Para executar o Docker sem SUDO:
$ sudo usermod -aG docker $USER
```

### Como executar o ambiente:

```bash
# Clona a aplicação do GitHub
$ git clone https://github.com/leonardopigatto/docker-laravel.git

# Acessa a pasta
$ cd docker-laravel

# Constroi e reconstroi os containers
$ sudo docker-compose build app

# Executa os containers (em background)
$ docker-compose up -d

# Encerra e remove os containers
$ docker-compose down
```

### Como executar comandos:

```bash
# Comandos
$ docker-compose exec app ..... (Ex: composer install, php artisan key:generate, ...)

# Acesso ao Terminal
$ docker-compose exec app /bin/bash
```

### Como criar/clonar/copiar uma aplicação Laravel:

- Clonar/copiar:
Coloque todos os seus arquivos da aplicação dentro da pasta `src`.

- Criar uma nova aplicação Laravel:
```bash
# Acessa a pasta src
$ cd src

# Cria um novo projeto Laravel
$ docker-compose exec app composer create-project laravel/laravel .
```

### Acesso:

- Para acessar: http://localhost:8080/.

- Para acessar o phpMyAdmin: http://localhost:8081/.

## :warning: Avisos

### MySQL

- Caso queira, mude o usuário, senha e banco de dados no arquivo `docker-compose.yml`.

- O MySQL está configurado de modo persistente, isto é, quando executar o comando `docker-compose down` os dados nele armazenados serão mantidos no diretório `./.docker/mysql`, caso não deseje utilizar esse recurso, basta excluir trecho de código abaixo do arquivo `docker-compose.yml`. Para excluir a pasta `mysql` é preciso ter permissões `sudo`.

```
volumes:
  - ./.docker/mysql:/var/lib/mysql
```

### phpMyAdmin

- Não se esqueça de configurar o usuário e senha no arquivo `docker-compose.yml` caso tenha alterado no MySQL.

### .env do Laravel

- Utilizar no campo `DB_HOST=db` e o usuário e senha configurados no MySQL.