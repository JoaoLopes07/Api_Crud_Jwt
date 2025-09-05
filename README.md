# API de Autenticação e CRUD com Node.js, MongoDB e JWT

API REST que registra/autentica usuários (JWT access + refresh) e expõe um CRUD protegido `/todos`.

## Stack
- Node.js + Express
- MongoDB + Mongoose
- JWT (access ~15min, refresh ~7d)
- Validação com Zod
- CORS básico + Helmet
- Bcrypt para hash de senha

## Rotas

### Autenticação
- `POST /auth/register` → `{ name, email, password }` → cria usuário com hash e retorna `{ user, accessToken, refreshToken }`
- `POST /auth/login` → `{ email, password }` → retorna `{ user, accessToken, refreshToken }`
- `POST /auth/refresh` → `{ refreshToken }` → retorna `{ accessToken, refreshToken, user }`

### Usuário
- `GET /me` → Header: `Authorization: Bearer <access>` → retorna `{ user }`

### Todos (protegido)
- `POST /todos` → `{ title, done? }` → cria
- `GET /todos` → lista apenas do usuário
- `GET /todos/:id` → busca por id (se pertencer ao usuário)
- `PUT /todos/:id` → `{ title?, done? }` → atualiza
- `DELETE /todos/:id` → remove

## Regras de segurança
- Access token expira em ~15 min (`JWT_ACCESS_EXPIRES`)
- Refresh token expira em ~7 dias (`JWT_REFRESH_EXPIRES`)
- Senhas **nunca** em texto claro (bcrypt)
- Rotas `/me` e `/todos*` protegidas por middleware
- CORS habilitado (básico)

## Como rodar localmente

1. **Pré-requisitos**: Node.js 18+, MongoDB rodando.
2. Clone/extraia o projeto e instale dependências:
   ```bash
   npm install
   ```
3. Crie um arquivo `.env` baseado em `.env.example`:
   ```env
   MONGODB_URI=mongodb://localhost:27017/node_auth_crud_jwt
   PORT=3000
   JWT_ACCESS_SECRET=troque-por-um-segredo-forte
   JWT_REFRESH_SECRET=troque-por-um-segredo-ainda-mais-forte
   JWT_ACCESS_EXPIRES=15m
   JWT_REFRESH_EXPIRES=7d
   ```
4. Inicie o servidor em desenvolvimento:
   ```bash
   npm run dev
   ```
   Servidor em: `http://localhost:3000`

## Modelos

### User
```ts
{
  _id: ObjectId,
  name: string,
  email: string (unique),
  passwordHash: string,
  tokenVersion: number,
  createdAt, updatedAt
}
```

### Todo
```ts
{
  _id: ObjectId,
  title: string,
  done: boolean,
  owner: ObjectId -> User,
  createdAt, updatedAt
}
```

## Estratégia de Refresh Token (stateless com versionamento)
- O `refreshToken` inclui `tv` (tokenVersion) do usuário.
- Ao chamar `/auth/refresh`, validamos o token e comparamos `tv` com o `tokenVersion` atual do usuário.
- Para invalidar refresh tokens antigos (logout global), basta incrementar `tokenVersion` do usuário (rota administrativa opcional).

## Testes com Postman/Insomnia
Importe a collection `postman_collection.json` e configure as variáveis:
- `baseUrl` (ex.: http://localhost:3000)
- `accessToken` e `refreshToken` serão preenchidos automaticamente via scripts.

## Licença
MIT
