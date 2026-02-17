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

## Para Linux e Windows: Customize a Montagem
troque a linha 9:

```
 -v "/MUDE/PARA_PASTA/DO_SEU/PC/:/home/container" \

```
para uma pasta no seu PC, já antecipadamente criada de rodar o docker run.\
É desta forma que poderemos manipular os arquivos locais do server sem uso do\
terminal/powershell

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
## Autenticação

Aqui já temos o container criado e o server rodando, na teoria está rodando, precisamos autenticar
nossa copia original do jogo para ele ser um server, sendo assim entre no container:

```
docker attach hytale-server

```
Dentro do container rode comando de autenticação:

```
/auth login device

```
Siga as instruções na tela, ao finalizar para manter a autenticação funcionando automaticamente, execute no console:

```
/auth persistence Encrypted

```
Desta forma a autenticação não só fica encriptada, mas fica persistente, a cada reboot/restart do container não sendo necessario autenticar novamente.

Qualquer duvida veja o FAQ oficial:

https://support.hytale.com/hc/en-us/articles/45326769420827-Hytale-Server-Manual

## Comandos Uteis

Iniciar o Server:

```
docker container start hytale-server

```

Reiniciar o Server:

```
docker container restart hytale-server

```

Parar o Server:

```
docker container restart hytale-server

```

# Atualizar Server Hytale em modo Release:

o Hytale está em acesso antecipado, mesmo após suas atualizações são constantes, assim que o client atualiza para o mais recente,
ele não acessa nenhum server que não está na versão mais atual, sendo assim, ao ter um novo release de versão temos que atualizar:

## Acesse a pasta que o server está:
cd /sua/pasta/aonde_o_jogo_esta_instalado/pasta_do_server/game/

Cada um instala na pasta que quiser, porem a pasta padrão sempre será a ../game/
Nesta pasta temos que ver se já está baixado o server downloander, para linux e windows, se ausente
baixe aqui: https://support.hytale.com/hc/en-us/articles/45326769420827-Hytale-Server-Manual

Procure o download após "A command-line tool to download Hytale server and asset files with OAuth2 authentication."

## Linux

No terminal, estando na pasta ../game/ como no exempo abaixo;

```
cd /sua/pasta/aonde_o_jogo_esta_instalado/pasta_do_server/game/

```
agora execute o updater:

```
./hytale-downloader-linux-amd64  /sua/pasta/aonde_o_jogo_esta_instalado/pasta_do_server/game/Assets.zip

```

exemplo da execução:

```
downloading latest ("release" patchline) to "2026.02.17-255364b8e.zip"
[==================================================] 100.0% (1.4 GB / 1.4 GB)B)
validating checksum...
successfully downloaded "release" patchline (version 2026.02.17-255364b8e)
```

Inicie o server, se ainda dizer que está versão anterior, pare o server, dezipe o Assets.zip
dentro da pasta game,substitua os arquivos e inicie o server novamente.

# Duvidas?
Qualquer dúividas abra algo em Issues!
