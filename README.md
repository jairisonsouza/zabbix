# Zabbix Docker Compose Setup

Este repositório contém a configuração do Zabbix utilizando o Docker Compose. O Zabbix é uma plataforma de monitoramento poderosa que oferece monitoramento em tempo real de servidores, redes e dispositivos de rede.

## Arquitetura

A configuração do Docker Compose inclui os seguintes serviços:

1. **PostgreSQL (Banco de Dados)**
2. **Zabbix Server**
3. **Zabbix Web (Interface Web)**
4. **Zabbix Agent**
5. **Zabbix SNMP Traps**

Todos os serviços estão conectados por uma rede Docker chamada `zabbix-net`.

## Pré-requisitos

Antes de iniciar a instalação, certifique-se de ter o Docker e o Docker Compose instalados em seu sistema.

1. [Instalar o Docker](https://docs.docker.com/get-docker/)
2. [Instalar o Docker Compose](https://docs.docker.com/compose/install/)

## Instalação

### Passo 1: Clone o Repositório

Clone este repositório para sua máquina local:

```bash
git clone https://github.com/seu-usuario/zabbix-docker.git
cd zabbix-docker
```

## Passo 2: Configuração do Arquivo .env
Crie um arquivo .env na raiz do repositório com as variáveis de ambiente necessárias. O arquivo deve conter as seguintes variáveis:

```bash
POSTGRES_DB_USER=usuario_do_banco
POSTGRES_DATABASE=nome_do_banco
POSTGRES_DB_PASSWORD=senha_do_banco
```

## Passo 3: Iniciar os Contêineres
Com o Docker e o Docker Compose configurados, inicie os serviços com o seguinte comando:
```
docker-compose up -d
```
Esse comando irá iniciar os contêineres em segundo plano. Os serviços que serão iniciados são:

* postgres-zabbix: Banco de dados PostgreSQL.
* zabbix-server: Servidor Zabbix, que se conecta ao banco de dados PostgreSQL.
* zabbix-web: Interface web do Zabbix (acessível via http://localhost:8080).
* zabbix-agent: Agente Zabbix para monitoramento local.
* zabbix-snmptraps: Serviço para captura de SNMP traps.

## Passo 4: Acessar a Interface Web
Após os contêineres estarem em execução, você pode acessar a interface web do Zabbix em:
```
http://localhost
```

As credenciais padrão para login são:

Usuário: Admin
Senha: zabbix

## Passo 5: Parar os Contêineres
Para parar todos os serviços em execução, use o comando:
```
docker-compose down
```

## Passo 6: (Opcional) Verificar Logs
Se necessário, você pode verificar os logs dos contêineres para depuração:
```
docker-compose logs -f
```