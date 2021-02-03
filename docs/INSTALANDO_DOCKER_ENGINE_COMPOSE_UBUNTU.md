# Instalando Docker Engine & Compose (Ubuntu)

Por Douglas Miguel, 03 de Fevereiro de 2021 

## Instalando Docker Engine

&nbsp;

### Removendo versões antigas

Versões mais antigas do Docker eram chamadas `docker`, `docker.io` ou `docker-engine`

```
$ sudo apt-get remove docker docker-engine docker.io containerd runc
```

&nbsp;

### Instalando usando o repositório

&nbsp;

**1.** Atualize o índice de pacotes do `apt` 

```
$ sudo apt-get update
```

&nbsp;

**2.** Instale os pacotes para permitir que o `apt` use um repositório HTTPS

```
$ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
```

&nbsp;

**3.** Adicione a chave GPG oficial da Docker

```
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

Verifique se você possui a chave com essa assinatura `9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88`, procurando pelos últimos 8 caracteres da assinatura:

```
$ sudo apt-key fingerprint 0EBFCD88
```

Saída semelhante a:

```
pub   rsa4096 2017-02-22 [SCEA]
      9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
uid           [ unknown] Docker Release (CE deb) <docker@docker.com>
sub   rsa4096 2017-02-22 [S]
```

&nbsp;

**4.** Use o seguinte comando para configurar o repositório `stable`

```
$ sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```

Atualize o índice de pacotes do `apt`, novamente:

```
$ sudo apt-get update
```

&nbsp;

**5.** Instale a versão mais atualizada do `Docker Engine`  e `containerd.io`

```
$ sudo apt-get install docker-ce docker-ce-cli containerd.io
```

Se quiser instalar uma **versão específica** do `Docker Engine`, liste as versões disponíveis no repositório:

```
$ apt-cache madison docker-ce
```

Saída semelhante a:

```
docker-ce | 5:18.09.1~3-0~ubuntu-xenial | https://download.docke...
docker-ce | 5:18.09.0~3-0~ubuntu-xenial | https://download.docke...  
```

Instale a **versão específica** usando a `VERSION_STRING` da segunda coluna, por exemplo, `5:18.09.0~3-0~ubuntu-xenial`:

```
$ sudo apt-get install docker-ce=<VERSION_STRING> docker-ce-cli=<VERSION_STRING> containerd.io
```

&nbsp;

**6.** Verifique se o `Docker Engine` foi instalado corretamente executando a imagem `hello-world`.

```
$ sudo docker run hello-world
```

Se não quiser usar comandos `docker` com `sudo` (como mostrado acima) crie o grupo `docker`:

```
$ sudo groupadd docker
```

Adicione o seu usuário ao grupo `docker`:

```
$ sudo usermod -aG docker $USER
```

Ative as alterações do grupo:

```
$ newgrp docker
```

Verifique se consegue rodar comandos `docker` sem `sudo`:

```
$ docker run hello-world
```

&nbsp;

## Instalando Docker Compose

**1.** Instale o `curl`

```
$ sudo apt install curl
```

&nbsp;

**2.** Baixe a última versão `stable` do `Docker Compose`
 
```
$ sudo curl -L "https://github.com/docker/compose/releases/download/1.28.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

Se quiser instalar uma **versão diferente**, substitua `1.28.2` para a versão que você quer usar.

&nbsp;

**3.** Transforme o binário baixado em executável

```
$ sudo chmod +x /usr/local/bin/docker-compose
```

**Nota:** Se o comando `docker-compose` falhar após instalação, verifique seu `path`. Você também pode criar um link simbólico para `/usr/bin` ou qualquer outro diretório no seu `path`, por exemplo:

```
$ sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```

&nbsp;

**4.** Teste a instalação

```
$ docker-compose --version
```

&nbsp;

## Dúvidas, críticas ou sugestões

Slack: Douglas Miguel

Email: douglas.miguel@docket.com.br

&nbsp;

## Referências

- Install Docker Engine on Ubuntu: https://docs.docker.com/engine/install/ubuntu
- Install Docker Compose: https://docs.docker.com/compose/install/