# 📚 Projeto Flask: Sistema de Autenticação e API

Um projeto educacional completo em Python com **Flask** que demonstra conceitos essenciais de desenvolvimento web: autenticação, APIs RESTful e frontend interativo.

**Ideal para aprender:** Python, Flask, APIs, HTML/CSS/JavaScript, Banco de Dados, Segurança Web

---

## 🎯 Funcionalidades

- ✅ **Sistema de Login/Registro** - Autenticação com senhas criptografadas
- ✅ **API RESTful** - Endpoints para CRUD (Create, Read, Update, Delete)
- ✅ **Frontend Responsivo** - Interface HTML/CSS/JavaScript
- ✅ **Banco de Dados** - SQLite para persistência de dados
- ✅ **Tokens JWT** - Autenticação de requisições à API
- ✅ **Validação de Dados** - Segurança em formulários

---

## 📋 Requisitos

- Python 3.8+
- pip (gerenciador de pacotes)
- Navegador web moderno

---

## 🚀 Instalação

### 1. Clone ou crie o projeto
```bash
mkdir meu-projeto-flask
cd meu-projeto-flask
```

### 2. Crie um ambiente virtual
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# Linux/Mac
python3 -m venv venv
source venv/bin/activate
```

### 3. Instale as dependências
```bash
pip install -r requirements.txt
```

### 4. Execute a aplicação
```bash
python app.py
```

Acesse: **http://localhost:5000**

---

## 📁 Estrutura do Projeto

```
projeto-flask/
│
├── app.py                 # Arquivo principal (Flask app)
├── requirements.txt       # Dependências do projeto
├── database.db           # Banco de dados SQLite (criado automaticamente)
│
├── templates/            # Arquivos HTML (Frontend)
│   ├── index.html        # Página inicial
│   ├── login.html        # Formulário de login
│   ├── register.html     # Formulário de registro
│   └── dashboard.html    # Painel do usuário
│
└── static/               # Arquivos estáticos
    └── style.css         # Estilos CSS
```

---

## 🔧 Como Usar

### 1. Criar uma Conta
1. Acesse `http://localhost:5000/register`
2. Preencha nome de usuário e senha
3. Clique em "Registrar"

### 2. Fazer Login
1. Acesse `http://localhost:5000/login`
2. Digite suas credenciais
3. Será redirecionado ao dashboard

### 3. Usar a API

#### Registro (POST)
```bash
curl -X POST http://localhost:5000/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"username":"joao","password":"senha123"}'
```

#### Login (POST)
```bash
curl -X POST http://localhost:5000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"username":"joao","password":"senha123"}'
```

Retorna um **token JWT** que deve ser usado em outras requisições:
```json
{
  "token": "eyJ0eXAiOiJKV1QiLCJhbGc..."
}
```

#### Obter Perfil (GET)
```bash
curl -X GET http://localhost:5000/api/user/profile \
  -H "Authorization: Bearer SEU_TOKEN_AQUI"
```

#### Atualizar Perfil (PUT)
```bash
curl -X PUT http://localhost:5000/api/user/profile \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer SEU_TOKEN_AQUI" \
  -d '{"email":"joao@email.com"}'
```

---

## 💡 Conceitos Aprendidos

| Conceito | Descrição | Localização |
|----------|-----------|-------------|
| **Rotas (Routes)** | Mapeamento de URLs para funções | `@app.route()` |
| **Métodos HTTP** | GET, POST, PUT, DELETE | Decoradores de rota |
| **Templates Jinja2** | Renderização dinâmica de HTML | `templates/` |
| **Autenticação** | Login e sessões de usuário | `@login_required` |
| **APIs RESTful** | Endpoints JSON para acesso externo | `/api/` |
| **Banco de Dados** | CRUD com SQLAlchemy | `User` model |
| **Criptografia** | Hashing de senhas com Werkzeug | `generate_password_hash()` |
| **Validação** | Verificação de dados de entrada | Forms Flask-WTF |
| **Cookies/Sessões** | Manutenção de estado do usuário | `session` |

---

## 🔐 Recursos de Segurança

### Senhas Criptografadas
```python
from werkzeug.security import generate_password_hash, check_password_hash

# Criar hash
hash = generate_password_hash("minha_senha")

# Verificar
check_password_hash(hash, "minha_senha")  # True
```

### CSRF Protection
```python
from flask_wtf.csrf import CSRFProtect
csrf = CSRFProtect(app)
```

### JWT para APIs
```python
import jwt
token = jwt.encode({'user_id': 1}, 'SECRET', algorithm='HS256')
```

---

## 📝 Arquivos Principais

### `app.py` - Aplicação Principal
Contém:
- Configuração do Flask
- Definição de modelos (User)
- Rotas de autenticação (`/login`, `/register`)
- Rotas do API (`/api/...`)
- Inicialização do banco de dados

### `templates/login.html` - Formulário de Login
- Coleta username e password
- Envia dados via POST
- Valida campos no frontend

### `templates/dashboard.html` - Painel do Usuário
- Exibe informações do usuário
- Permite atualizar perfil
- Faz requisições AJAX à API

### `static/style.css` - Estilos
- Layout responsivo
- Design moderno
- Dark/Light mode (opcional)

---

## 🎓 Exercícios de Aprendizado

### Nível 1 - Iniciante
1. [ ] Criar uma rota que retorna "Olá, [nome]!"
2. [ ] Adicionar um campo de email no cadastro
3. [ ] Exibir email no dashboard

### Nível 2 - Intermediário
4. [ ] Implementar logout
5. [ ] Adicionar validação de email (regex)
6. [ ] Criar rota para deletar conta

### Nível 3 - Avançado
7. [ ] Implementar recuperação de senha
8. [ ] Adicionar autenticação de 2 fatores
9. [ ] Criar painel admin
10. [ ] Implementar rate limiting

---

## 🐛 Troubleshooting

### Erro: "ModuleNotFoundError: No module named 'flask'"
```bash
pip install flask
```

### Erro: "Address already in use"
Flask já está rodando em outra janela. Feche-a ou use outra porta:
```bash
python app.py --port 5001
```

### Banco de dados corrompido
Delete `database.db` e execute novamente:
```bash
rm database.db
python app.py
```

---

## 📚 Recursos Adicionais

- [Documentação Flask](https://flask.palletsprojects.com)
- [SQLAlchemy ORM](https://docs.sqlalchemy.org)
- [JWT Auth](https://pyjwt.readthedocs.io)
- [Flask-Login](https://flask-login.readthedocs.io)
- [REST API Best Practices](https://restfulapi.net)

---

## 🤝 Contribuindo

Sugestões de melhorias:
- Adicionar testes unitários (pytest)
- Implementar logging
- Dockerizar a aplicação
- Adicionar documentação Swagger/OpenAPI
- Deploy em Heroku ou AWS

---

## 📄 Licença

Este projeto é educacional e de código aberto.

---

## 👨‍💻 Autor

Criado para fins educacionais - Aprenda Python com Flask!

**Dúvidas?** Consulte a documentação ou fórum da comunidade Python.

---

## 🚀 Próximos Passos

Depois de dominar este projeto, estude:
- ✅ Testes automatizados (unittest, pytest)
- ✅ Microsserviços com Flask
- ✅ Deploy em produção
- ✅ Docker e containerização
- ✅ Frontend moderno (React, Vue)
- ✅ Banco de dados relacional (PostgreSQL)
