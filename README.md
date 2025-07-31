# Estudo de Autenticação JWT

Projeto de estudo para aplicar e compreender conceitos de autenticação JWT com Node.js, Express e TypeScript.

## 📋 Sobre o Projeto

Este é um projeto educacional focado no aprendizado de:

- 🔐 **Autenticação JWT** - Como implementar e validar tokens
- 🛡️ **Middleware de autorização** - Controle de acesso baseado em roles
- 📝 **Proteção de rotas** - Implementação de endpoints públicos e privados
- ⚡ **TypeScript** - Tipagem estática para maior segurança
- 🚀 **Express.js** - Estruturação de APIs REST

## 🛠️ Tecnologias Utilizadas

- **Node.js** - Runtime JavaScript
- **Express.js** - Framework web
- **TypeScript** - Superset tipado do JavaScript
- **JWT (jsonwebtoken)** - Autenticação via tokens
- **TSX** - Executor TypeScript para desenvolvimento

## 📁 Estrutura do Projeto

```
src/
├── configs/          # Configurações da aplicação
│   └── auth.ts       # Configuração JWT
├── controllers/      # Controladores da aplicação
│   ├── products-controller.ts
│   └── sessions-controller.ts
├── middlewares/      # Middlewares customizados
│   ├── ensureAuthenticated.ts
│   └── verifyUserAuthorization.ts
├── routes/          # Definição das rotas
│   ├── index.ts
│   ├── products.routes.ts
│   └── sessions.routes.ts
├── types/           # Definições de tipos TypeScript
├── utils/           # Utilitários e helpers
└── server.ts        # Arquivo principal do servidor
```

## 🚀 Como Executar o Projeto

### Pré-requisitos

- Node.js (versão 16 ou superior)
- npm ou yarn

### Instalação

1. Clone o repositório:
```bash
git clone <url-do-repositorio>
cd estudo-jwt
```

2. Instale as dependências:
```bash
npm install
```

3. Configure as variáveis de ambiente:
```bash
cp .env-example .env
```

4. Edite o arquivo `.env` e adicione sua chave secreta:
```env
AUTH_SECRET=sua_chave_secreta_aqui
```

5. Execute o projeto em modo de desenvolvimento:
```bash
npm run dev
```

O servidor estará rodando em `http://localhost:3333`

## 🔑 API Endpoints

### Autenticação

#### POST `/sessions`
Realiza login e retorna um token JWT.

**Body:**
```json
{
  "username": "rodrigo",
  "password": "123456"
}
```

**Response:**
```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
```

### Produtos

#### GET `/products`
Lista todos os produtos (acesso público).

#### POST `/products`
Cria um novo produto (requer autenticação e role `sale` ou `admin`).

**Headers:**
```
Authorization: Bearer <token>
```

## 🛡️ Sistema de Autorização

O template inclui um sistema de autorização baseado em roles:

- **costumer**: Usuário padrão
- **sale**: Pode criar produtos
- **admin**: Acesso total

### Middlewares Disponíveis

- `ensureAuthenticated`: Verifica se o usuário está autenticado
- `verifyUserAuthorization`: Verifica se o usuário tem as permissões necessárias

## 📝 Usuário de Teste

Para fins de estudo, existe um usuário fake configurado no código:

- **Username:** rodrigo
- **Password:** 123456
- **Role:** costumer

> ⚠️ **Importante**: Este é apenas um usuário hardcoded para fins educacionais. Em um projeto real, você integraria com um banco de dados e usaria hash nas senhas.

## 🔧 Configuração JWT

O token JWT é configurado com:
- Expiração: 1 dia
- Secret: Definido via variável de ambiente `AUTH_SECRET`

## 📚 Scripts Disponíveis

- `npm run dev`: Executa o projeto em modo de desenvolvimento com hot reload

## 📚 Conceitos Aprendidos

Este projeto aborda os seguintes conceitos importantes:

### 🔐 JWT (JSON Web Token)
- Estrutura de um token JWT (Header, Payload, Signature)
- Como gerar e assinar tokens
- Validação e verificação de tokens
- Configuração de expiração

### 🛡️ Middlewares de Segurança
- `ensureAuthenticated`: Validação de token JWT
- `verifyUserAuthorization`: Controle de acesso baseado em roles
- Tratamento de erros de autenticação

### 🚪 Controle de Acesso
- Rotas públicas vs protegidas
- Sistema de roles/permissões
- Headers de autorização (Bearer Token)

## 🎯 Para Estudar

### Testando a API
1. Faça login para obter um token:
```bash
curl -X POST http://localhost:3333/sessions \
  -H "Content-Type: application/json" \
  -d '{"username": "rodrigo", "password": "123456"}'
```

2. Use o token para acessar rotas protegidas:
```bash
curl -X POST http://localhost:3333/products \
  -H "Authorization: Bearer SEU_TOKEN_AQUI" \
  -H "Content-Type: application/json"
```

### Pontos de Atenção
- ⚠️ **Senhas em texto plano**: Para estudo apenas! Use bcrypt em produção
- ⚠️ **Usuário hardcoded**: Integre com banco de dados real
- ⚠️ **Secret simples**: Use secrets mais complexos e seguros

## 🔮 Evoluções Possíveis

Para aprofundar o estudo, considere implementar:

- [ ] **Hash de senhas** com bcrypt
- [ ] **Banco de dados** (PostgreSQL, MongoDB)
- [ ] **Refresh tokens** para renovação automática
- [ ] **Validação de dados** com Joi ou Zod
- [ ] **Rate limiting** para prevenir ataques
- [ ] **Logs de segurança**
- [ ] **Testes automatizados**

## 📄 Licença

Este projeto está sob a licença ISC - veja o arquivo `package.json` para detalhes.

---

📖 **Projeto desenvolvido para fins educacionais e estudo de conceitos de autenticação JWT**