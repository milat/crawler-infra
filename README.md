# crawler-infra
Infra conteinerizada para projetos de crawler.

## Utilização:

### 0. Certifique-se que possua o [docker](https://docs.docker.com/engine/install/ubuntu/) e o [docker-compose](https://docs.docker.com/compose/install/) instalados.

### 1. Criar e configurar o arquivo *.env* baseado no arquivo *.env.example*.

A variável *PROJECTS_PATH* deve informar o caminho até o diretório que os projetos estão instalados.

A variável *RESTART_POLICY* deve informar a política de reinicialização e inicialização *on boot* dos containers, sendo aceito os valores: 
- always (sempre irá re/iniciar o container automaticamente).
- unless-stopped (sempre irá re/iniciar o container automaticamente, ao menos que o container tenha sido parado manualmente).
- on-failure:*x* (irá re/iniciar o container até *x* vezes automaticamente (trocar *x* por número inteiro) em caso de falha).
- no (nunca irá re/iniciar o container automaticamente).

### 2. Subir a aplicação:

```
docker-compose up -d
```

Após subir os containers uma vez, para que qualquer alteração que vier a fazer nas configurações tenha efeito, você deve rebuildar o(s) container(s) ao subir:

```
docker-compose up -d --build
```

### 3. Verificando o status dos containers:
```
docker ps
```

### 4. Acessando o container:
```
# docker exec -ti <nome_container> bash

docker exec -ti crawler-php bash
```

### 5. Restartando os containers
```
docker-compose restart
```

### 6. Parando os containers
```
docker-compose stop
```


### 7. Verificando o LOG dos containers

Para verificar as últimas linhas geradas no log:

```
# docker logs <nome_container>

docker logs crawler-php
```

Para determinar quantas linhas do log serão exibidas:

```
# docker logs <nome_container> -n <quantidade_linhas>

docker logs crawler-php -n 5
```

Para acompanhar o log em tempo real (o terminal ficará preso até pressionar *ctrl+c*):

```
# docker logs <nome_container> -f

docker logs crawler-mysql -f
```

#### Obs: Todos os comandos acima devem ser executado fora dos containers, na raiz onde este projeto está instalado.

### Serviços disponíveis:

- PHP 5.6;
- MySql 5.7;

### Author
- [Antonio Milat](https://github.com/milat)