# Environment

Motivação: o trabalho envolvido na instalação do rabbitmq e postgres

## Requisitos

Para utilizar esse repositório é preciso ter instalado apenas o `docker` e `docker-compose`

Veja o passo a passo: [Instalando Docker Engine & Compose](docs/INSTALANDO_DOCKER_ENGINE_COMPOSE_UBUNTU.md)

&nbsp;

## Serviços

| Serviço | Porta | Versão | ID |
| -	| -	| -	| - |
| RabbitMQ | 5672 | 3-management-alpine | docket-rabbitmq |
| RabbitMQ Management | 15672 | 3-management-alpine | docket-rabbitmq |
| PostgreSQL | 5432 | 13-alpine | docket-postgres |
| pgAdmin4 | 16543 | 4.30 | docket-pgadmin4 |

&nbsp;

## Executando

- Clone ou baixe este repositório na sua maquina
- Abra um terminal na raiz do diretorio
- Siga os passos abaixo

&nbsp;

Para rodar todos serviços disponíveis:
```
$ docker-compose up
```

&nbsp;

Para rodar serviços específicos indique os ID's dos serviços **separado por espaço**:
```
$ docker-compose up ID_SERVICO1 ID_SERVICO2
```

&nbsp;

Para rodar em segundo plano adicione o parametro `-d` ao comando:
```
$ docker-compose up -d ID_SERVICO1 ID_SERVICO2
```

&nbsp;

Para parar todos serviços:
```
$ docker-compose stop
```

&nbsp;

Para parar serviços específicos indique os ID's dos serviços **separado por espaço**:
```
$ docker-compose stop ID_SERVICO1 ID_SERVICO2
```

&nbsp;

## Restaurando backups

Você pode fazer o `restore` de um `backup` normalmente através do pgAdmin4, mas existe um limite de 50mb de tamanho por arquivo.

O diretório `backups` é vinculado ao container do postgres, ou seja, qualquer alteração feita na maquina será refletida dentro do container.

&nbsp;

Para fazer o restore de um backup:
```
docker exec docket-postgres pg_restore -U postgres -d docket /backups/<nome_arquivo>.backup
```
