# Docker Reference Card

## Dockerfile

## Docker CLI

### Docker Hub
| Command | Description |
| --- | --- |
```docker login -u "<user>" docker.io``` | Faz o login em um registro
```docker logout ``` | Faz o logout em um registro
```docker push <user>/<repository>:<tag>``` | Envia ou leva uma imagem a um registry (push)
```docker pull <user>/<repository>:<tag>``` | Traz ou busca uma imagem de um registro (pull)
```docker search <term>``` |	Faz uma pesquisa no Docker Hub em busca de imagens com o termo especificado (term)

### Containers
| Command | Description |
| --- | --- |
```docker build -t <user>/<repository>:<tag> .``` | Constrói uma imagem a partir de um Dockerfile (arquivo Docker) no diretório atual 
```docker run --rm -it --name=<container> --entrypoint=<command> <user>/<repository>:<tag>```|
```docker rm container```	| Remove um container que está rodando
```docker start container```	| Inicia um novo container
```docker stop container```	| Encerra (stop) um container
```docker pause container```	| Pausa um container
```docker unpause container```	| Encerra a pausa de um container
```docker restart container```	| Reinicia um container
```docker wait container```	| Bloqueia um container
```docker export container```	| Exporta conteúdos de um container para um arquivo tar 
```docker attach container```	| Anexa conteúdo a um container que já está rodando (running container)
```docker wait container```	| Coloca processo em aguardo até que o container esteja terminado e enem exibe o exit code (código de saída)
```docker commit -m “commit message” -a “author” container username/image_name:tag```	| Salva um container que está rodando em formato de imagem
```docker logs -ft container```	| Acompanha logs de um container (registros)
```docker exec -ti container script.sh```	| Roda um comando em um container
```docker commit container image```	| Cria uma nova imagem a partir de um container
```docker create image```	| Cria um novo container a partir de uma imagem
```docker ps```	| Lista todos os containers que estão rodando (running containers)
```docker ps -a```	| Lista todos os containers
```docker diff container```	| Inspeciona alterações em diretórios e arquivos do sistema de arquivos do container
```docker top container```	| Exibe todos os processos que estão rodando em um container ativo
```docker logs container```	| Reúne os registros (logs) de um container
```docker stats container``` | Exibe as estatísticas de consumo de recursos de um container 

### Images

| Command | Description |
| --- | --- |
```docker image ls```	| Lista imagens
```docker image rm``` | image	Remove uma imagem
```docker image rm mysql```	| Remove uma imagem
```docker tag image tag```	| Rotula uma imagem (insere tag)
```docker history image```	| Exibe o histórico de uma imagem
```docker image prune```	| Remove uma imagem que não está sendo utilizada
```docker image prune -a```	| Remove todas as imagens que não estão sendo usadas por containers


### Parâmetros docker run

| Command | Description |
| --- | --- |
```–detach , -d```	| Roda um container no plano de fundo (background) e imprime a ID do container 
```--rm``` | apaga o container após a execução
```--it``` | modo interativo, executando o --entrypoint
```--name <container>``` | nome da instância
```-v <path>``` | monta um volume na instância a partir de uma pasta local
```--cpus=<int>```  |
```--memory=<int>g``` |
```--env-file <file>``` | Cria variáveis de ambiente
```-p <int>:<int>``` | Mapeia portas local:container
```–workdir , -w```	| Configura um diretório de trabalho em um container

### Services
| Command | Description |
| --- | --- |
```docker service ls```	| Lista todos os serviços que estão rodando em um swarm
```docker stack services stackname```	| Lista todos os serviços que estão rodando
```docker service ps servicename```	| Lista a tarefa (task) de um serviço
```docker service update servicename``` |	Atualiza um serviço
```docker service create image``` | Cria um novo serviço
```docker service scale servicename=10```	| Dimensiona um ou mais serviços replicados
```docker service logs stackname servicename```	| Lista todos os registros (logs) de serviços


### Networking
| Command | Description |
| --- | --- |
```docker network create networkname```	| Cria uma nova rede (new network)
```docker network rm networkname```	| Remove uma rede específica
```docker network ls```	| Lista todas as redes
```docker network connect networkname container```	|Conecta um container a uma rede
```docker network disconnect networkname container```	| Desconecta um container de uma rede
```docker network inspect networkname```	| Exibe informações detalhadas sobre a rede (network)


## Local Registry


