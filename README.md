# Environment

Motivação: o trabalho envolvido na instalação do rabbitmq e postgres

## Requisitos

Para utilizar esse repositório é preciso ter instalado apenas o `docker` e `docker-compose`

Veja o passo a passo: [Instalando Docker Engine & Compose](docs/INSTALANDO_DOCKER_ENGINE_COMPOSE_UBUNTU.md)

&nbsp;

## Serviços disponíveis

| Serviço    	| Versão              	| ID            	|
|------------	|---------------------	|-----------------	|
| RabbitMQ   	| 3-management-alpine 	| docket-rabbitmq 	|
| PostgreSQL 	| 13-alpine           	| docket-postgres 	|
| pgAdmin4   	| 4.30                	| docket-pgadmin4 	|

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