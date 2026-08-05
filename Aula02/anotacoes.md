## SGBD
Instalar e configurar o SGBD postgresql

Comando paea instalar o SGBD: 
```Bash
sudo apt install -y postgresql
```
>Obs: O comando sudo, no nosso caso, pode ser omitido pois já somos root.
---
Realizando verificação do SGBD:
```BASH
pg_lsclusters
```

Para realizar o acesso ao SGBD **sem senha**, utilizxar o comando:

```bash
sudo -u postgres psql
```
>Com esse comando o acesso é feito sem senha, pois o Linux já povou que você é (root).
Autenticação PEER.

Para primeiro acesso, alterei a senha:

```sql
ALTER USER postegres PASSWORD 'P0LLY4NN4@1008' ;
```

>O retorno correo, é `ALTER ROLE`.

Para sair ddo postgres, comando `\q` (igual o \quit de vários jogos).

```mermaid
graph LR
A[sudo -u postgres psql]--<b>Autenticação</b>-->B[Só funcion entrendo dentro do próorio Linux(Ubuntu, Debian)]
```

```mermaid
graph LR
A[sudo psql -h 127.0.0.1 -U postgres]--<b>Autenticação</b>-->B[Funciona vindo de qualquer máquina, porém é necessário inseriri a senha]
```
---
## Configurações de serviço
>Caminho padão para as configura POSTGRESQL
![alt text](image.png)

Primeira configuração:
```bash
sudo nano postgresql.conf
```
CLTL + W para buscar a linha do listen_addresses e decomentamos, alterando para `*`.

Se ficar localhost, somente o meu PC acessa.

Passo 2:
```bash
sudo nano pg_hba.conf
```
Nas últimas linhas, adicionei:
host all all 10.87.38/24 scram-sha-256

Para criar um banco de dados, usamos o comando:
```sql
CREATE DATABASE lojamax;

``` 
Para visualizar os bancos:
```bash
\l
```
