# Fullstack Auth Template

Um template completo de autenticação para aplicações Node.js com Express, TypeScript e JWT.

## 📋 Sobre o Projeto

Este é um template de autenticação robusto que inclui:

- 🔐 Autenticação JWT
- 🛡️ Middleware de autorização baseado em roles
- 📝 Sistema de produtos com controle de acesso
- ⚡ TypeScript para type safety
- 🚀 Express.js como framework web

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
cd fullstack-auth-template
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

Para fins de demonstração, existe um usuário fake configurado:

- **Username:** rodrigo
- **Password:** 123456
- **Role:** costumer

## 🔧 Configuração JWT

O token JWT é configurado com:
- Expiração: 1 dia
- Secret: Definido via variável de ambiente `AUTH_SECRET`

## 📚 Scripts Disponíveis

- `npm run dev`: Executa o projeto em modo de desenvolvimento com hot reload

## 🤝 Contribuindo

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

## 📄 Licença

Este projeto está sob a licença ISC. Veja o arquivo `package.json` para mais detalhes.

## 🔮 Próximos Passos

- [ ] Integração com banco de dados
- [ ] Hash de senhas com bcrypt
- [ ] Refresh tokens
- [ ] Validação de dados com Joi ou Zod
- [ ] Testes unitários e de integração
- [ ] Documentação da API com Swagger

---

⭐ Se este template foi útil para você, considere dar uma estrela no repositório!