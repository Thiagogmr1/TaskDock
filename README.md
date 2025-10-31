# Projeto Lista de Tarefas - Docker

Autor: **Thiago Gabriel Marques Rodrigues**

Estudante de Engenharia de Software — Fábrica de Tecnologias Turing (FTT)

Este projeto demonstra a conteinerização de uma aplicação web simples (frontend + backend) utilizando Docker e Docker Compose.

---

## Antes de rodar o projeto, clone o repositório do GitHub para sua máquina local:

```bash
# Clonar o repositório
git clone https://github.com/oLopesAlvaro/tarefas-docker.git

# Entrar na pasta do projeto
cd tarefas-docker
```
---

# Estrutura da Aplicação

- Frontend: Aplicação em Vite/JavaScript, servida via Nginx.

- Backend: API em Node.js/Express, responsável por gerenciar as      tarefas.

- Banco de Dados: PostgreSQL, utilizado para armazenar as tarefas.

---

## Como rodar o projeto

1. **Construir e subir os containers:**
```bash

docker compose up --build 

> com o comando acima, você inicializa a aplicação interira (frontend + backend + banco de dados) 

> Para parar a aplicação, use: 
docker compose down

```
---

2. *Acesso às portas:*

Frontend → http://localhost:8080

Backend → http://localhost:3001

---

3. *Containers:*

| Serviço   | Porta | Descrição                      |
|-----------|-------|--------------------------------|
| frontend  | 8080  | Interface web servida via Nginx|
| backend   | 3001  | API Node.js/Express            |
| postgres  | 5432  | Banco de dados PostgreSQL      |

---

4. ### Em casos de erros:

**1º Erro**: *Error response from daemon: Conflict. The container name "/postgres" is already in use.*

rode:
```bash

# Remove o container antigo que está em conflito
docker rm -f postgres

# Depois, suba os containers normalmente
docker compose up --build
```

**2º Erro**: *Falha ao conectar com o PostgreSQL. A aplicação operará em modo "em memória". Motivo: getaddrinfo ENOTFOUND postgres*

rode: 
```bash

# Verifica se o container do postgres está rodando
docker ps

# Se não estiver, inicie ele manualmente
docker compose up -d postgres

# Depois, suba o restante dos containers
docker compose up --build

```
---



