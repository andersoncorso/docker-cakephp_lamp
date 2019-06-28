# Docker LAMP para Cakephp 3
Ambiente Docker com Apache, MySQL, PHPMyadmin e Mailhog configurado para trabalhar com o framework CakePHP 3. 
Obs: Ambiente desenvolvido para trabalho local e testes, não recomendado para o uso em servidores de aplicação pública.


### Primeira execução

```console
docker-compose -f "docker-compose.yml" up -d --build
```

### Conectando no container

```console
docker-compose exec container-php /bin/bash
```

## Comandos dentro do container

- Caso queira executar algum comando após a aplição ser executada em uma imagem docker, basta adicionar como prefixo do comando:
```console
docker-compose exec container-php $nome_do_comando
```

Exemplo:

- Migration:
```console
docker-compose exec container-php bin/cake migrations migrate
```
