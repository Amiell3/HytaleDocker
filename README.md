# Hytale Server:Docker
Server em Docker para o Hytale com biding mount.
\
Tendo o biding mount configurado, você poderá manipular os arquivos do server de forma mais facil,\
para instalação de mods, plugins e outras tarefas que exijam copiar, colar, substituir e atualizar\
o server, sem necessidade de usar exclusivamente pelo terminal/powershell

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
Instale o Docker e corra o comando no powershell como administrador:


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
# Autenticação

Para Autenticar sua conta como um server, siga as instruções oficiais:

https://support.hytale.com/hc/en-us/articles/45326769420827-Hytale-Server-Manual

