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

### Estados (status) de um container

- up : container em execução
- paused : container pausado. Quando o container esta pausado nao consume CPU, mas ocupa memoria
- docker pause id_do_container : pausar container
- docker unpause id_do_container : remover o container do pause "voltar a rodar"
- docker stop id_do_container : parar execução do container
- docker start id_do_container : voltar a executar um container que estava parado
