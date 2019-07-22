# Docker LAMP para Cakephp 3
Ambiente Docker com Apache, MySQL, PHPMyadmin e Mailhog configurado para trabalhar com o framework CakePHP 3. 
Obs: Ambiente desenvolvido para trabalho local e testes, não recomendado para o uso em servidores de aplicação pública.


## Configuração

- No arquivo '.env', configure o nome prefixo do seu container e use o mesmo para o mysql-host;
```console
# CONTAINER
NAME_PREFIX=container

# MySQL config
MYSQL_HOST=container-mysql
```


### Primeira execução

```console
docker-compose -f "docker-compose.yml" up -d --build
```

### Conectando no container

```console
docker-compose exec php /bin/bash
```

## Comandos dentro do container

- Caso queira executar algum comando após a aplição ser executada em uma imagem docker, basta adicionar como prefixo do comando:
```console
docker-compose exec php $nome_do_comando
```

Exemplo:

- Instalar novo projeto CakePHP (apague a pasta "app" antes de executar o comando):
```console
docker-compose exec php composer -d app create-project --prefer-dist cakephp/app app
```
- Migration:
```console
docker-compose exec php bin/cake migrations migrate
```


### Comandos Docker ;)

- Stop all container:
```console
docker stop $(docker ps -a -q)
```

- Delete all containers:
```console
docker rm $(docker ps -a -q)
```

- Delete all images:
```console
docker rmi $(docker images -q)
```