# Sistema Vendas Laravel

Aplicação web de gestão de vendas construída com Laravel 10, PHP e JavaScript. O sistema permite registrar usuários, cadastrar clientes e produtos, e gerenciar vendas com CRUD completo.

---

## 📋 Funcionalidades principais

### Autenticação
- ✅ Login de usuário
- ✅ Cadastro de novo usuário
- ✅ Logout

### Gestão de Clientes
- ✅ Listar todos os clientes
- ✅ Cadastrar novo cliente
- ✅ Visualizar detalhes do cliente
- ✅ Editar dados do cliente
- ✅ Excluir cliente

### Gestão de Produtos
- ✅ Listar todos os produtos
- ✅ Cadastrar novo produto
- ✅ Visualizar detalhes do produto
- ✅ Editar informações do produto
- ✅ Excluir produto

### Gestão de Vendas
- ✅ Listar todas as vendas
- ✅ Criar nova venda
- ✅ Visualizar detalhes da venda
- ✅ Editar venda
- ✅ Excluir venda
- ✅ Gestão de parcelas
- ✅ Gestão de itens da venda

---

## 🛠️ Tecnologias

| Tecnologia | Versão |
|-----------|--------|
| **PHP** | 8.1.7 |
| **Laravel** | 10.48.3 |
| **Node.js** | 18.14.1 |
| **Vite** | - |
| **Bootstrap** | - |
| **AdminLTE** | - |

---

## 📦 Pré-requisitos

Antes de começar, certifique-se de ter instalado:

- PHP 8.1 ou superior
- Composer
- Node.js 18+
- npm ou yarn
- MySQL ou outro banco de dados relacional

---

## 🚀 Instalação

### 1. Clone o repositório
```bash
git clone https://github.com/seu-usuario/sistema-vendas-laravel.git
cd sistema-vendas-laravel
```

### 2. Instale as dependências PHP
```bash
composer install
```

### 3. Instale as dependências Node.js
```bash
npm install
```

### 4. Configure o arquivo de ambiente
```bash
cp .env.example .env
```

### 5. Gere a chave da aplicação
```bash
php artisan key:generate
```

### 6. Configure o banco de dados
Edite o arquivo `.env` e configure suas credenciais de banco de dados:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=vitvendas
DB_USERNAME=root
DB_PASSWORD=sua_senha
```

### 7. Execute as migrations
```bash
php artisan migrate
```

### 8. (Opcional) Popule o banco com dados iniciais
```bash
php artisan db:seed
```

### 9. Compile os ativos frontend
```bash
npm run dev
```

Para produção:
```bash
npm run build
```

### 10. Inicie o servidor Laravel
```bash
php artisan serve
```

A aplicação estará disponível em `http://localhost:8000`

---

## 📂 Estrutura do Projeto

```
vitvendas/
├── app/
│   ├── Http/
│   │   ├── Controllers/
│   │   │   ├── LoginController.php
│   │   │   ├── ClienteController.php
│   │   │   ├── ProdutoController.php
│   │   │   └── VendaController.php
│   │   └── Kernel.php
│   ├── Models/
│   │   ├── User.php
│   │   ├── Cliente.php
│   │   ├── Produto.php
│   │   ├── Venda.php
│   │   ├── Itens_Venda.php
│   │   └── Parcela.php
│   └── Providers/
├── database/
│   ├── migrations/
│   └── seeders/
├── resources/
│   ├── views/
│   │   ├── login/
│   │   ├── cliente/
│   │   ├── produto/
│   │   ├── venda/
│   │   └── layout/
│   ├── css/
│   └── js/
├── routes/
│   └── web.php
├── public/
├── config/
├── composer.json
├── package.json
└── vite.config.js
```

---

## 🔐 Autenticação

O sistema utiliza autenticação nativa do Laravel com middleware `auth`. Rotas protegidas:

- `/cliente` - Gestão de clientes
- `/produto` - Gestão de produtos
- `/venda` - Gestão de vendas

Rotas públicas:

- `/` - Login
- `/registrar` - Registro de novo usuário

---

## 🌐 Rotas Principais

### Autenticação
```
GET  /              → Página de login
POST /auth          → Autenticar usuário
GET  /registrar     → Página de registro
POST /store         → Criar novo usuário
POST /logout        → Fazer logout
```

### Clientes
```
GET    /cliente              → Lista de clientes
GET    /cliente/novo         → Formulário criar cliente
POST   /cliente/store        → Salvar novo cliente
GET    /cliente/{id}         → Visualizar cliente
GET    /cliente/editar/{id}  → Formulário editar cliente
PUT    /cliente/update/{id}  → Atualizar cliente
GET    /cliente/remover/{id} → Excluir cliente
```

### Produtos
```
GET    /produto              → Lista de produtos
GET    /produto/novo         → Formulário criar produto
POST   /produto/store        → Salvar novo produto
GET    /produto/{id}         → Visualizar produto
GET    /produto/editar/{id}  → Formulário editar produto
PUT    /produto/update/{id}  → Atualizar produto
GET    /produto/remover/{id} → Excluir produto
```

### Vendas
```
GET    /venda              → Lista de vendas
GET    /venda/novo         → Formulário criar venda
POST   /venda/store        → Salvar nova venda
GET    /venda/{id}         → Visualizar venda
GET    /venda/editar/{id}  → Formulário editar venda
PUT    /venda/update/{id}  → Atualizar venda
GET    /venda/remover/{id} → Excluir venda
```

---

## 💾 Modelos e Banco de Dados

### Modelo de Dados

**Usuários (users)**
- id
- name
- email
- password
- email_verified_at
- created_at
- updated_at

**Clientes (cliente)**
- id
- cpf
- nome
- email
- celular
- cep
- bairro
- logradouro
- numero
- complemento
- cidade
- uf
- created_at
- updated_at

**Produtos (produto)**
- id
- titulo
- valor
- descricao
- created_at
- updated_at

**Vendas (venda)**
- id
- client_id
- forma_pagamento
- total_venda
- created_at
- updated_at

**Parcelas (parcela)**
- id
- venda_id
- numero_parcela
- valor
- status_pagamento
- data_vencimento
- created_at
- updated_at

**Itens da Venda (itens_venda)**
- id
- venda_id
- produto_id
- quantidade
- valor_unitario
- created_at
- updated_at

---

## 🔧 Desenvolvimento

### Compilar CSS/JS em tempo real
```bash
npm run dev
```

### Executar testes
```bash
php artisan test
```

### Limpar cache
```bash
php artisan cache:clear
php artisan config:cache
```

---

## 📝 Notas Importantes

- Certifique-se de que o diretório `storage/` tem permissões de escrita
- O arquivo `.env` não deve ser commitado no repositório
- Use variáveis de ambiente para dados sensíveis (chaves de API, credenciais de banco, etc.)

---

## 🤝 Contribuindo

Sinta-se livre para enviar pull requests e issues para melhorias.

---

## 📄 Licença

Este projeto é licenciado sob a MIT License.

---

## 👨‍💻 Autor

Sistema de Vendas Laravel

---

**Última atualização:** 17 de abril de 2026
