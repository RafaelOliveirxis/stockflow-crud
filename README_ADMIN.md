# StockFlow — versão administrativa

## Stack
- Node.js + Express
- SQLite com better-sqlite3
- bcryptjs para senha
- express-session para sessão administrativa
- HTML, CSS e JavaScript no frontend

## Recursos
- Login administrativo
- Dashboard com indicadores e distribuição por categoria
- CRUD de produtos
- Controle de estoque
- Categorias
- Histórico/auditoria de alterações
- Banco de dados SQLite

## Executar
1. Instale Node.js.
2. Execute `npm install`.
3. Execute `npm start`.
4. Abra `http://localhost:3000/login.html`.

### Acesso demonstrativo
E-mail: `admin@stockflow.local`
Senha: `admin123`

> Para produção, altere a senha inicial e o SESSION_SECRET. O banco `stockflow.db` é criado automaticamente e não deve ser versionado.