# Docker

- imagem é o arquivo onde estão ás configurações
- container é uma abstração de uma imagem

## Comandos docker

- docker ps : lista todos os containers rodando
- docker ps -a : lista todos os containers incluindo os que nao estão em execução
- docker image ls : lista todas ás imagens dockers baixadas
- docker build -t api -f nome_do_arquivo : fazer build de Dockerfile. "-t" nome da imagem, "-f" nome do arquivo, "." arquivo Dockerfile padrão. Criar imagem docker
- docker build -t api . : fazer build de Dockerfile na raiz
- docker run -p 3333:3333 nome_da_imagem : rodando o container. "-p" mapeamento da porta 3333 da imagem para 3333 do computador. O container pode ser rodado pelo nome ou id
- docker run -p 3333:3333 -d id_da_imagem : "-d" executando em background para liberar o terminal.
- docker logs id_do_container : ver as logs do container
- docker history nome_da_imagem : visualizar o histórico da imagem
- docker rm id_do_container : remover container
- docker rm -f id_do_container : forçar a remoção de um container
- docker rmi id_da_imagem : remover uma imagem
- docker rmi -f id_da_imagem : forçar a remoção de uma imagem

- docker build -t nome_da_imagem:v1 : tag para versionar imagem
- docker run -p 3333:3333 -d nome_da_image:v1 : rodar versão específica de uma imagem

- docker container prune : remover todos os containers na máquina de uma só vez

### Estados (status) de um container

- up : container em execução
- paused : container pausado. Quando o container esta pausado nao consume CPU, mas ocupa memoria
- docker pause id_do_container : pausar container
- docker unpause id_do_container : remover o container do pause "voltar a rodar"
- docker stop id_do_container : parar execução do container
- docker start id_do_container : voltar a executar um container que estava parado

## Volumes

Containers são projetados para serem descartáveis e podem ser facilmente parados, destruídos ou substituídos.
Portanto, se for preciso armazenar dados, é recomendado utilizar ambiente externo ao container.

Volumes são diretórios/locais onde os dados dos containers são armazenados.

O container e o volume têm responsabilidades completamente separadas, mas é possível vincular "e é o certo a ser feito".

É possível usar o mesmo volume em containers diferentes.

- docker exec -it id_do_container bash : abrir o diretório de trabalho onde está rodando o container. "bash" é a shell, podem ser usadas outras
- docker exec -it id_do_container sh : abrir o diretório de trabalho onde está rodando o container
- docker exec -it id_do_container //bin/sh : abrir o diretório de trabalho onde está rodando o container

- docker container inspect id_do_container : inspecionar um container

### Comandos para volumes

- docker volume create nome_do_volume : criar volume
- docker volume inspect nome_do_volume : inspecionar um volume
- docker run -v api-volume:/usr/src/app -p 3333:3333 -d api : criar container e definir volume. "-v" definir o nome do volume
- docker volume ls : listar volumes
- docker volume rm nome_do_volume : remover volume

## Docker Compose

- É um arquivo com especificações de todos os containers necessário para app.

O Docker Compose é uma ferramenta usada para definir e executar aplicações de vários contêineres do Docker.

No Compose, um Arquivo YAML é usado para configurar os serviços do aplicativo. Em seguida, você cria e inicia todos os serviços com base na sua configuração executando um só comando.
