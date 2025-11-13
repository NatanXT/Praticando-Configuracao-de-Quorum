# Praticando-Configuracao-de-Quorum
Criar o ambiente do Quorum//Subir o ambiente do Quorum local

# Guia para a instalação -- Ambiente Local Quorum (QuickStart)

Este documento explica como criar e rodar o ambiente Quorum local :

- 3 nós GoQuorum
- 3 nós Tessera (privacidade)
- Cakeshop (dashboard)
- docker-compose

## 1) Pré-rquisitos
instalar:

- Node.js
- Docker Desktop (e logar no Docker Hub)
- Em caso de Linux o fluxo é diferente.

## 2) Instalar o Quorum Wizard 

- npm install -g quorum-wizard

ver se instalou mesmo :
- quorum-wizard --version

## 3) Criar o projeto Quorum

Na pasta que vc quiser: 
- quorum-wizard

Escolha as opções:
- Quickstart (3-node raft network with tessera and cakeshop)
- dicker-compose
- Yes (substituir se aparecer)

O wizard vai gerar a pastas:
- network/3-nodes-quickstart

## 4) Entrar na pasta do ambiente

- cd network/3-nodes-quickstart

## 5) Subir sua rede quorum

- docker-compose up -d

verificar o conteiner: 
- docker ps

vai ver algo como:

CONTAINER ID   IMAGE                               COMMAND                  CREATED         STATUS                   PORTS                                                                                                                                         NAMES
3b3098cc9fe4   quorumengineering/quorum:21.4.0     "/bin/sh -c 'UDS_WAI…"   3 minutes ago   Up 3 minutes (healthy)   0.0.0.0:22000->8545/tcp, [::]:22000->8545/tcp, 0.0.0.0:23000->8546/tcp, [::]:23000->8546/tcp, 0.0.0.0:24000->8547/tcp, [::]:24000->8547/tcp   node1-3-nodes-quickstart     
32886bd064cc   quorumengineering/quorum:21.4.0     "/bin/sh -c 'UDS_WAI…"   3 minutes ago   Up 3 minutes (healthy)   0.0.0.0:22001->8545/tcp, [::]:22001->8545/tcp, 0.0.0.0:23001->8546/tcp, [::]:23001->8546/tcp, 0.0.0.0:24001->8547/tcp, [::]:24001->8547/tcp   node2-3-nodes-quickstart     
306d01a31b28   quorumengineering/quorum:21.4.0     "/bin/sh -c 'UDS_WAI…"   3 minutes ago   Up 3 minutes (healthy)   0.0.0.0:22002->8545/tcp, [::]:22002->8545/tcp, 0.0.0.0:23002->8546/tcp, [::]:23002->8546/tcp, 0.0.0.0:24002->8547/tcp, [::]:24002->8547/tcp   node3-3-nodes-quickstart     
9254df3e9f4d   quorumengineering/tessera:21.1.1    "/bin/sh -c 'DDIR=/q…"   3 minutes ago   Up 3 minutes (healthy)   0.0.0.0:9081->9080/tcp, [::]:9081->9080/tcp ...

Ai vc procura algo como: 
- quorum-node1
- quorum-node2
- quorum-node3
- txmanager1 (Tessera)
- txmanager2
- txmanager3
- cakeshop

## 6) Acessar o dashboard (da Cakeshop)

abrir o navegador e colar:
- http://localhost:8999

## 7) Testar o nó 1 da blockchain

Entrar no container:
- docker exec -it quorum-node1 geth attach

Consulte o numero do bloco:
- eth.blockNumber

se aparecer qualquer numero de resposta, é porque está ativa a rede.

## 8) Parar a rede

- docker-compose down