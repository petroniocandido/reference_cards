# Docker Reference Card

## Dockerfile

## Docker CLI

| Command | Description |
| --- | --- |
```docker login -u "<user>" docker.io``` | 
```docker build -t <user>/<repository>:<tag> .``` |
```docker push <user>/<repository>:<tag>``` |
```docker run --rm -it --name=<container> --entrypoint=<command> <user>/<repository>:<tag>``` |


### Parâmetros docker run

| Command | Description |
| --- | --- |
--rm | apaga o container após a execução
--it | modo interativo, executando o --entrypoint
--name <container> | nome da instância
-v <path> | monta um volume na instância a partir de uma pasta local
--cpus=<int>  |
--memory=<int>g |
--env-file <file> | Cria variáveis de ambiente
-p <int>:<int> | Mapeia portas local:container
