# HytaleDocker
Server em Docker para o Hytale com biding mount 

## Obsservação:
Não sou dev, sou apenas uma curiosa, então as instruções podem não estar da melhor forma ou
melhor documentadas, apenas fiz do jeito que aprendi e conheço e

NÃO RODA COM COPIAS PIRATAS,\
se quiser fazer isso, procure outro local :D

## Para Linux e Windows Customize a Montagem
troque a linha 9:

```
 -v "/MUDE/PARA_PASTA/DO_SEU/PC/:/home/container" \

```
para uma pasta no seu PC, já antecipadamente criada de rodar o docker run.

## Windows
Instale o Docker e corra o comando no powershell:


```
docker run \
  --name hytale-server \
  -e SERVER_IP="0.0.0.0" \
  -e SERVER_PORT="5520" \
  -e PROD="FALSE" \
  -e DEBUG="FALSE" \
  -e TZ="America/Sao_Paulo" \
  -p 5520:5520/udp \
  -v "/MUDE/PARA_PASTA/DO_SEU/PC/:/home/container" \
  -v "/etc/machine-id:/etc/machine-id:ro" \
  --restart unless-stopped \
  -t -i \
  deinfreu/hytale-server:experimental

```

## Linux Atomic

Para quem usa linux atomic como:
- Fedora Silverblue
- Bazzite
- Aurora
- Bluefin
- Endless OS
- Fedora Atomic
- NixOS
- openSUSE MicroOS
- Torizon OS
- Vanilla OS

Você precisa declarar a unidade Z na linha 9:

```
 -v "/MUDE/PARA_PASTA/DO_SEU/PC/:/home/container:Z" \

```

Ficando assim:

```
docker run \
  --name hytale-server \
  -e SERVER_IP="0.0.0.0" \
  -e SERVER_PORT="5520" \
  -e PROD="FALSE" \
  -e DEBUG="FALSE" \
  -e TZ="America/Sao_Paulo" \
  -p 5520:5520/udp \
  -v "/MUDE/PARA_PASTA/DO_SEU/PC/:/home/container:Z" \
  -v "/etc/machine-id:/etc/machine-id:ro" \
  --restart unless-stopped \
  -t -i \
  deinfreu/hytale-server:experimental

```

## Linux (Exceto Atomic)

```
docker run \
  --name hytale-server \
  -e SERVER_IP="0.0.0.0" \
  -e SERVER_PORT="5520" \
  -e PROD="FALSE" \
  -e DEBUG="FALSE" \
  -e TZ="America/Sao_Paulo" \
  -p 5520:5520/udp \
  -v "/MUDE/PARA_PASTA/DO_SEU/PC/:/home/container" \
  -v "/etc/machine-id:/etc/machine-id:ro" \
  --restart unless-stopped \
  -t -i \
  deinfreu/hytale-server:experimental
```
