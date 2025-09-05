🚀 Node Auth CRUD JWT

Projeto Node.js + Express com autenticação via JWT e operações CRUD.
Inclui gerenciamento de usuários, tarefas (todos), validações, conexão com banco de dados e suporte a Docker.

✨ Funcionalidades

Registro e login de usuários

Autenticação com JWT

Rotas protegidas por middleware

CRUD de tarefas (Todos)

Validação de dados de entrada

Arquivo Postman Collection para testes

Configuração via .env

Suporte a Docker Compose

📂 Estrutura do Projeto
src/
 ├── config/          # Configurações da aplicação
 ├── middlewares/     # Autenticação e outros middlewares
 ├── models/          # Modelos de dados (User, Todo)
 ├── routes/          # Rotas (auth, todos, me)
 ├── utils/           # Funções auxiliares (JWT, etc.)
 ├── validators/      # Schemas de validação
 ├── db.js            # Conexão com banco de dados
 └── server.js        # Inicialização do servidor

⚙️ Como Usar
# Clonar repositório
git clone https://github.com/seu-usuario/node-auth-crud-jwt.git
cd node-auth-crud-jwt

# Instalar dependências
npm install

# Configurar variáveis de ambiente
cp .env.example .env

# Rodar servidor em desenvolvimento
npm run dev


Servidor disponível em: http://localhost:3000

Usando Docker
docker-compose up -d

📌 Rotas Principais
Método	Rota	Descrição
POST	/auth/register	Registrar usuário
POST	/auth/login	Login e token JWT
GET	/me	Dados do usuário logado
GET	/todos	Listar tarefas
POST	/todos	Criar tarefa
PUT	/todos/:id	Atualizar tarefa
DELETE	/todos/:id	Remover tarefa
🧪 Testes

Importe o arquivo postman_collection.json no Postman para testar rapidamente todas as rotas.

📜 Licença

Distribuído sob a licença MIT.
