Node Auth CRUD JWT

Projeto Node.js + Express com autenticação via JWT e operações CRUD.
Inclui gerenciamento de usuários, tarefas (todos), validações, conexão com banco de dados e suporte a Docker.

🚀 Funcionalidades

Registro e login de usuários

Autenticação com JSON Web Token (JWT)

Rotas protegidas por middleware de autenticação

CRUD de Todos (tarefas)

Validação de dados de entrada

Arquivo Postman Collection para testar endpoints

Configuração com variáveis de ambiente

Suporte a Docker Compose

📂 Estrutura de Pastas
src/
 ├── config/          # Configurações da aplicação
 ├── middlewares/     # Middlewares (ex: autenticação)
 ├── models/          # Modelos de dados (User, Todo)
 ├── routes/          # Rotas (auth, todos, me)
 ├── utils/           # Utilitários (JWT, etc.)
 ├── validators/      # Schemas de validação
 ├── db.js            # Conexão com o banco de dados
 └── server.js        # Inicialização do servidor

🛠 Tecnologias Utilizadas

Node.js

Express

JWT

[Mongoose ou Sequelize]* para banco de dados

Docker

Postman
 para testes

*Ajustar conforme o banco usado (MongoDB ou PostgreSQL).

⚙️ Instalação e Uso
1. Clonar repositório
git clone https://github.com/seu-usuario/node-auth-crud-jwt.git
cd node-auth-crud-jwt

2. Instalar dependências
npm install

3. Configurar variáveis de ambiente

Copiar o arquivo .env.example para .env e preencher com suas credenciais:

cp .env.example .env

4. Rodar em desenvolvimento
npm run dev


Servidor rodará em:
👉 http://localhost:3000

5. Usando Docker (opcional)
docker-compose up -d

📌 Rotas Principais
Autenticação

POST /auth/register → Registrar usuário

POST /auth/login → Login e geração de token

Usuário

GET /me → Retorna dados do usuário logado

Todos

GET /todos → Lista todas as tarefas

POST /todos → Cria uma nova tarefa

PUT /todos/:id → Atualiza tarefa

DELETE /todos/:id → Remove tarefa

🧪 Testes via Postman

Importe o arquivo postman_collection.json no Postman para testar as rotas rapidamente.

📜 Licença

Este projeto é distribuído sob a licença MIT.
