# StockFlow — Sistema Administrativo de Produtos e Estoque

> Projeto acadêmico independente do TCC/KoraMarketplace.

## 📌 Sobre
O StockFlow é um sistema web administrativo para cadastro, consulta, alteração e exclusão de produtos, controle de estoque, categorias, autenticação, dashboard e histórico de alterações.

A versão atual evoluiu do CRUD inicial com LocalStorage para uma arquitetura com **Node.js + Express + SQLite + API REST + autenticação por sessão**.

## 🎯 Objetivo
Desenvolver uma aplicação administrativa simples, responsiva e organizada, demonstrando conceitos de Desenvolvimento Web, Banco de Dados, CRUD, APIs, autenticação, controle de estoque e versionamento.

## 🚀 Funcionalidades

### 🔐 Login
- Login administrativo por e-mail e senha.
- Sessão protegida.
- Logout.
- Senhas armazenadas com hash bcrypt.
- Proteção das rotas administrativas.

### 📊 Dashboard
- Total de produtos.
- Total de unidades em estoque.
- Valor total do estoque.
- Gráfico de produtos por categoria.
- Lista de produtos com estoque baixo.
- Acesso rápido ao cadastro.

### 📦 Produtos
- Cadastro.
- Consulta.
- Pesquisa.
- Filtro por categoria.
- Ordenação por nome, preço e estoque.
- Alteração.
- Exclusão.
- Preço e quantidade.
- Imagem por URL.
- Alerta de estoque baixo.

### 🗂️ Categorias
- Listagem.
- Criação.
- Exclusão.
- Bloqueio de exclusão quando existem produtos vinculados.

### 📋 Histórico
O sistema registra:
- Produtos criados.
- Produtos alterados.
- Produtos excluídos.
- Estoque atualizado.
- Categorias criadas e excluídas.
- Usuário responsável.
- Data e hora.

## 🛠️ Tecnologias

**Frontend**
- HTML5
- CSS3
- JavaScript

**Backend**
- Node.js
- Express.js
- Express Session
- bcryptjs

**Banco de dados**
- SQLite
- better-sqlite3

**Versionamento**
- Git
- GitHub

## 🏗️ Arquitetura

    FRONTEND
    HTML + CSS + JavaScript
            |
         HTTP/JSON
            |
            v
    BACKEND
    Node.js + Express
            |
           SQL
            |
            v
    BANCO DE DADOS
    SQLite

## 🗄️ Banco de dados

O banco é criado automaticamente na primeira execução.

### usuarios
id, nome, email, senha, perfil e criado_em.

### categorias
id, nome e criado_em.

### produtos
id, nome, categoria_id, preco, estoque, imagem, criado_em e atualizado_em.

### historico
id, usuario_id, produto_id, acao, detalhes e criado_em.

Relacionamentos:
- Um produto pertence a uma categoria.
- Um registro de histórico pode estar associado a um usuário.
- Um registro de histórico pode estar associado a um produto.

## 🔌 API REST

### Autenticação

| Método | Endpoint | Função |
|---|---|---|
| POST | /api/login | Login |
| POST | /api/logout | Logout |
| GET | /api/me | Sessão atual |

### Produtos

| Método | Endpoint | Função |
|---|---|---|
| GET | /api/produtos | Listar |
| POST | /api/produtos | Criar |
| PUT | /api/produtos/:id | Alterar |
| DELETE | /api/produtos/:id | Excluir |
| PATCH | /api/produtos/:id/estoque | Atualizar estoque |

### Categorias

| Método | Endpoint | Função |
|---|---|---|
| GET | /api/categorias | Listar |
| POST | /api/categorias | Criar |
| DELETE | /api/categorias/:id | Excluir |

### Dashboard e histórico

| Método | Endpoint | Função |
|---|---|---|
| GET | /api/dashboard | Indicadores |
| GET | /api/historico | Auditoria |

## 📁 Estrutura

    stockflow-crud/
    ├── index.html
    ├── login.html
    ├── produtos.html
    ├── cadastro.html
    ├── categorias.html
    ├── historico.html
    ├── server.js
    ├── css/
    │   └── style.css
    ├── js/
    │   ├── app.js
    │   ├── admin.js
    │   └── dashboard.js
    ├── img/
    ├── package.json
    ├── .gitignore
    ├── README.md
    └── README_ADMIN.md

O arquivo stockflow.db é criado localmente e está no .gitignore.

## 💻 Instalação

### Pré-requisitos
- Node.js
- npm
- Git

Verifique:

    node -v
    npm -v
    git --version

### Clonar

    git clone https://github.com/RafaelOliveirxis/stockflow-crud.git
    cd stockflow-crud

### Instalar dependências

    npm install

### Executar

    npm start

Acesse:

    http://localhost:3000/login.html

## 🔑 Acesso demonstrativo

E-mail: admin@stockflow.local

Senha: admin123

> Para produção, altere a senha inicial e configure um SESSION_SECRET seguro por variável de ambiente.

## 🧪 Fluxo de demonstração

1. Entrar no sistema.
2. Visualizar o dashboard.
3. Criar uma categoria.
4. Cadastrar um produto.
5. Consultar o produto.
6. Alterar preço ou estoque.
7. Verificar o alerta de estoque baixo.
8. Consultar o histórico.
9. Excluir um produto.
10. Conferir o registro da ação.
11. Fazer logout.

## 📱 Responsividade

O sistema foi preparado para:
- Computadores.
- Notebooks.
- Tablets.
- Smartphones.

Inclui menu mobile, grids adaptáveis, formulários responsivos e tabelas com rolagem quando necessário.

## 📊 Requisitos funcionais

- **RF01:** permitir login administrativo.
- **RF02:** cadastrar produtos.
- **RF03:** consultar e pesquisar produtos.
- **RF04:** alterar produtos.
- **RF05:** excluir produtos.
- **RF06:** criar e gerenciar categorias.
- **RF07:** controlar estoque.
- **RF08:** apresentar dashboard.
- **RF09:** registrar histórico.
- **RF10:** funcionar em diferentes tamanhos de tela.

## ⚙️ Requisitos não funcionais

- Interface simples e intuitiva.
- Organização visual.
- Persistência em banco de dados.
- Senhas protegidas por hash.
- Controle de sessão.
- Responsividade.
- Código organizado.
- Versionamento com Git.

## 🔒 Segurança

A aplicação utiliza hash de senha com bcrypt, sessão HTTP com cookie httpOnly, proteção básica das rotas administrativas, validações e exclusão do banco local do versionamento.

Para produção, recomenda-se adicionar HTTPS, CSRF, rate limiting, recuperação de senha, controle de permissões, logs de segurança, backups e migrações.

## 🧪 Testes

| Teste | Resultado esperado |
|---|---|
| Login válido | Acesso ao painel |
| Login inválido | Acesso recusado |
| Cadastro | Produto salvo no banco |
| Alteração | Dados atualizados |
| Exclusão | Produto removido |
| Categoria | Categoria criada |
| Categoria em uso | Exclusão bloqueada |
| Estoque baixo | Alerta exibido |
| Dashboard | Indicadores carregados |
| Histórico | Ações registradas |
| Logout | Sessão encerrada |
| Acesso sem login | Redirecionamento para login |
| Mobile | Interface adaptada |

## 🔄 Evolução

### Versão 1.0
CRUD, LocalStorage, pesquisa, filtros, responsividade e interface acadêmica.

### Versão 2.0
Backend Node.js, Express, SQLite, login, sessões, bcrypt, dashboard, gráfico, categorias, controle de estoque, API REST e histórico.

## 🎓 Aplicação acadêmica

O projeto demonstra:
- Desenvolvimento Web.
- CRUD.
- Banco de Dados.
- API REST.
- Arquitetura cliente-servidor.
- Autenticação.
- Modelagem de dados.
- Controle de estoque.
- Versionamento.
- Responsividade e UI.

## 👥 Equipe

- **Rafael Oliveira**
- Integrante 2
- Integrante 3
- Integrante 4
- Integrante 5

Substitua os nomes conforme a composição real do grupo.

## 📋 Checklist

- [x] Projeto independente do TCC/KoraMarketplace
- [x] CRUD completo
- [x] Pesquisa e filtros
- [x] Controle de estoque
- [x] Categorias
- [x] Login administrativo
- [x] Sessão
- [x] Banco de dados
- [x] API REST
- [x] Dashboard
- [x] Gráfico
- [x] Histórico
- [x] Responsividade
- [x] Menu mobile
- [x] Documentação
- [x] Repositório GitHub
- [ ] Inserir nomes reais dos integrantes
- [ ] Adicionar prints finais da apresentação

## 🌐 Repositório

https://github.com/RafaelOliveirxis/stockflow-crud

## 👨‍💻 Autor

**Rafael Oliveira — Projeto acadêmico, 2026.**

## 📄 Licença

Projeto desenvolvido para fins acadêmicos e educacionais.


## ✨ Melhorias da versão 2.1
- Dashboard conectado ao endpoint real de indicadores.
- Gráfico de distribuição por categoria e alerta de estoque baixo.
- Validação de nome, categoria, preço, estoque e URL de imagem no backend.
- Cookie de sessão com expiração e configuração segura em produção.
- Foreign keys do SQLite ativadas.
- Mensagens de erro mais claras.
- Dashboard, produtos, categorias e histórico integrados ao mesmo fluxo administrativo.
- Interface mobile refinada e navegação consistente.

## ▶️ Demonstração local
Use `npm install` e depois `npm start`. O sistema abre em `http://localhost:3000/login.html`.

**Atenção:** GitHub Pages sozinho não executa o `server.js`, porque o projeto possui backend Node.js. Para demonstrar o sistema completo, execute localmente ou publique o backend em um serviço Node compatível.
