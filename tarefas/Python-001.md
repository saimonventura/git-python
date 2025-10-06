# 🐍 Python-001: Setup Flask com Poetry e Virtual Environment

## 📚 Sobre esta Tarefa

Agora que você já sabe usar Git, vamos começar a trabalhar com Python! Nesta tarefa você aprenderá a:
- Instalar e configurar o Poetry (gerenciador de dependências Python)
- Criar e ativar um ambiente virtual (venv)
- Instalar Flask usando Poetry
- Criar a estrutura básica de um projeto Flask
- Configurar arquivos necessários para colaboração

## 🎯 Objetivo

Criar um projeto Flask na raiz desta pasta usando Poetry, que no futuro se tornará o repositório principal do sistema.

---

## 📋 Pré-requisitos

- Python 3.13+ instalado
- Git configurado (você já fez isso na tarefa anterior!)
- Tarefa Git-001 concluída

---

## 🛠️ Passo a Passo

### 1. Instalando o Poetry

O Poetry é uma ferramenta moderna para gerenciar dependências e ambientes virtuais em Python.

#### **No macOS:**
```bash
curl -sSL https://install.python-poetry.org | python3 -
```

#### **No Windows:**
```powershell
(Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | py -
```

#### **No Linux:**
```bash
curl -sSL https://install.python-poetry.org | python3 -
```

**Após a instalação, reinicie seu terminal!**

Para verificar se foi instalado corretamente:
```bash
poetry --version
```

---

### 2. Criando uma Nova Branch

Antes de começar, crie uma branch para esta tarefa:

```bash
git checkout main
git pull origin main
git checkout -b python-001-seu-nome
```

💡 **Substitua "seu-nome"** pelo seu nome. Exemplo: `python-001-joao-silva`

---

### 3. Inicializando o Projeto Python na Raiz

⚠️ **IMPORTANTE**: Vamos criar o projeto Flask na **raiz da pasta**, não dentro de `tarefas/`.

Na raiz do projeto (`/git-python/`), execute:

```bash
# Inicializar um projeto Poetry
poetry init
```

O Poetry fará algumas perguntas. Responda assim:

1. **Package name**: `git-python-system`
2. **Version**: `0.1.0`
3. **Description**: `Sistema web para aprender Git e Python`
4. **Author**: `Seu Nome <seu.email@exemplo.com>`
5. **License**: Pressione Enter (deixar em branco)
6. **Compatible Python versions**: `^3.13`
7. **Would you like to define your main dependencies interactively?**: `y` (yes)
8. **Search for package**: `flask`
9. **Enter package**: `flask`
10. **Would you like to define your development dependencies interactively?**: `n` (no)
11. **Do you confirm generation?**: `y` (yes)

---

### 4. Instalando as Dependências

```bash
# Instalar Flask e criar o ambiente virtual automaticamente
poetry install

# Adicionar Flask se não foi adicionado no passo anterior
poetry add flask

# Adicionar dependências de desenvolvimento
poetry add --group dev pytest black flake8 python-dotenv
```

---

### 5. Ativando o Ambiente Virtual

```bash
# Ativar o ambiente virtual do Poetry
poetry shell
```

Para sair do ambiente virtual posteriormente, use:
```bash
exit
```

---

### 6. Criando a Estrutura do Projeto Flask

Crie os seguintes arquivos e pastas na **raiz** do projeto:

```bash
# Criar estrutura de pastas
mkdir -p app/templates app/static/css app/static/js

# Criar arquivos principais
touch app/__init__.py
touch app/routes.py
touch run.py
touch .env
touch .gitignore
touch requirements.txt
```

---

### 7. Configurando os Arquivos

#### **app/__init__.py**
```python
from flask import Flask

def create_app():
    app = Flask(__name__)
    app.config['SECRET_KEY'] = 'dev-secret-key-change-in-production'
    
    from app.routes import main
    app.register_blueprint(main)
    
    return app
```

#### **app/routes.py**
```python
from flask import Blueprint, render_template

main = Blueprint('main', __name__)

@main.route('/')
def index():
    return render_template('index.html', title='Git & Python Learning System')

@main.route('/sobre')
def sobre():
    return render_template('sobre.html', title='Sobre o Projeto')
```

#### **app/templates/base.html**
```html
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{% if title %}{{ title }} - {% endif %}Git & Python System</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet">
    <link rel="stylesheet" href="{{ url_for('static', filename='css/style.css') }}">
</head>
<body>
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
        <div class="container">
            <a class="navbar-brand" href="{{ url_for('main.index') }}">🐍 Git & Python</a>
            <div class="navbar-nav">
                <a class="nav-link" href="{{ url_for('main.index') }}">Home</a>
                <a class="nav-link" href="{{ url_for('main.sobre') }}">Sobre</a>
            </div>
        </div>
    </nav>

    <main class="container mt-4">
        {% block content %}{% endblock %}
    </main>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
```

#### **app/templates/index.html**
```html
{% extends "base.html" %}

{% block content %}
<div class="row">
    <div class="col-md-12">
        <div class="jumbotron bg-primary text-white p-5 rounded">
            <h1 class="display-4">Bem-vindo ao Sistema Git & Python! 🚀</h1>
            <p class="lead">Sistema web para desenvolvedores COBOL aprenderem tecnologias modernas.</p>
            <hr class="my-4">
            <p>Este sistema foi criado como projeto de aprendizado usando Flask, Poetry e boas práticas de desenvolvimento.</p>
            <a class="btn btn-light btn-lg" href="{{ url_for('main.sobre') }}" role="button">Saiba Mais</a>
        </div>
    </div>
</div>

<div class="row mt-4">
    <div class="col-md-4">
        <div class="card">
            <div class="card-body">
                <h5 class="card-title">🔧 Git</h5>
                <p class="card-text">Controle de versão e colaboração em projetos.</p>
            </div>
        </div>
    </div>
    <div class="col-md-4">
        <div class="card">
            <div class="card-body">
                <h5 class="card-title">🐍 Python</h5>
                <p class="card-text">Linguagem moderna e versátil para desenvolvimento web.</p>
            </div>
        </div>
    </div>
    <div class="col-md-4">
        <div class="card">
            <div class="card-body">
                <h5 class="card-title">🌐 Flask</h5>
                <p class="card-text">Framework web minimalista e poderoso.</p>
            </div>
        </div>
    </div>
</div>
{% endblock %}
```

#### **app/templates/sobre.html**
```html
{% extends "base.html" %}

{% block content %}
<div class="row">
    <div class="col-md-12">
        <h1>Sobre o Projeto</h1>
        <p class="lead">Este é um sistema web desenvolvido para ensinar desenvolvedores COBOL a trabalhar com tecnologias modernas.</p>
        
        <h3>Tecnologias Utilizadas</h3>
        <ul>
            <li><strong>Python 3.8+</strong> - Linguagem de programação</li>
            <li><strong>Flask</strong> - Framework web</li>
            <li><strong>Poetry</strong> - Gerenciador de dependências</li>
            <li><strong>Bootstrap 5</strong> - Framework CSS</li>
            <li><strong>Git</strong> - Controle de versão</li>
        </ul>

        <h3>Funcionalidades</h3>
        <p>Este sistema está em desenvolvimento e terá funcionalidades para:</p>
        <ul>
            <li>Gerenciamento de tarefas de aprendizado</li>
            <li>Acompanhamento de progresso</li>
            <li>Documentação interativa</li>
            <li>Exemplos práticos de código</li>
        </ul>
    </div>
</div>
{% endblock %}
```

#### **app/static/css/style.css**
```css
body {
    background-color: #f8f9fa;
}

.jumbotron {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

.card {
    transition: transform 0.2s;
    margin-bottom: 20px;
}

.card:hover {
    transform: translateY(-5px);
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
}

.navbar-brand {
    font-weight: bold;
}
```

#### **run.py**
```python
from app import create_app

app = create_app()

if __name__ == '__main__':
    app.run(debug=True, host='0.0.0.0', port=5000)
```

#### **.env**
```
FLASK_APP=run.py
FLASK_ENV=development
FLASK_DEBUG=1
SECRET_KEY=dev-secret-key-change-in-production
```

#### **.gitignore**
```
# Byte-compiled / optimized / DLL files
__pycache__/
*.py[cod]
*$py.class

# C extensions
*.so

# Distribution / packaging
.Python
build/
develop-eggs/
dist/
downloads/
eggs/
.eggs/
lib/
lib64/
parts/
sdist/
var/
wheels/
pip-wheel-metadata/
share/python-wheels/
*.egg-info/
.installed.cfg
*.egg
MANIFEST

# PyInstaller
*.manifest
*.spec

# Installer logs
pip-log.txt
pip-delete-this-directory.txt

# Unit test / coverage reports
htmlcov/
.tox/
.nox/
.coverage
.coverage.*
.cache
nosetests.xml
coverage.xml
*.cover
*.py,cover
.hypothesis/
.pytest_cache/

# Translations
*.mo
*.pot

# Django stuff:
*.log
local_settings.py
db.sqlite3
db.sqlite3-journal

# Flask stuff:
instance/
.webassets-cache

# Scrapy stuff:
.scrapy

# Sphinx documentation
docs/_build/

# PyBuilder
target/

# Jupyter Notebook
.ipynb_checkpoints

# IPython
profile_default/
ipython_config.py

# pyenv
.python-version

# pipenv
Pipfile.lock

# PEP 582
__pypackages__/

# Celery stuff
celerybeat-schedule
celerybeat.pid

# SageMath parsed files
*.sage.py

# Environments
.env
.venv
env/
venv/
ENV/
env.bak/
venv.bak/

# Spyder project settings
.spyderproject
.spyproject

# Rope project settings
.ropeproject

# mkdocs documentation
/site

# mypy
.mypy_cache/
.dmypy.json
dmypy.json

# Pyre type checker
.pyre/

# IDE
.vscode/
.idea/
*.swp
*.swo

# macOS
.DS_Store
```

---

### 8. Gerando o requirements.txt para Compatibilidade

```bash
# Gerar requirements.txt para desenvolvedores que não usam Poetry
poetry export -f requirements.txt --output requirements.txt --without-hashes
```

---

### 9. Testando o Projeto

```bash
# Ativar o ambiente virtual (se não estiver ativo)
poetry shell

# Executar o projeto
python run.py
```

Abra seu navegador e acesse: `http://localhost:5000`

Você deve ver a página inicial do sistema funcionando! 🎉

---

### 10. Criando sua Documentação

Crie o arquivo `tarefas/python-001-seu-nome.md` e documente sua experiência:

```markdown
# Python-001: Setup Flask com Poetry

## Nome
[Seu nome aqui]

## Data
[Data de conclusão]

## Passos que segui

1. [Descreva cada passo que você seguiu]
2. [Inclua comandos que executou]
3. [Mencione dificuldades encontradas]

## Dificuldades encontradas

[Descreva qualquer problema que enfrentou]

## O que aprendi

[Explique com suas palavras o que você aprendeu sobre:]
- Poetry
- Ambientes virtuais
- Flask
- Estrutura de projetos Python

## Comandos utilizados

```bash
# Liste todos os comandos que você executou
# Exemplo:
# poetry init
# poetry add flask
# poetry shell
# python run.py
```

## Screenshots

[Se possível, adicione screenshots do sistema funcionando]
```

---

### 11. Fazendo Commit e Push

```bash
# Adicionar todos os arquivos
git add .

# Fazer commit
git commit -m "Python-001: Setup inicial do sistema Flask com Poetry

- Configurado Poetry como gerenciador de dependências
- Criada estrutura básica do Flask
- Adicionados templates HTML com Bootstrap
- Configurado ambiente de desenvolvimento
- Documentação da tarefa concluída"

# Enviar para o GitHub
git push origin python-001-seu-nome
```

---

### 12. Abrindo Pull Request

1. Acesse o GitHub e abra um Pull Request
2. **Título**: `Python-001: [Seu Nome] - Setup Flask com Poetry`
3. **Descrição**: Descreva o que você implementou e aprendeu

---

## ✅ Critérios de Conclusão

Sua tarefa Python-001 estará completa quando:

- [ ] Poetry instalado e configurado
- [ ] Projeto Flask criado na raiz da pasta
- [ ] Ambiente virtual funcionando
- [ ] Sistema Flask executando em localhost:5000
- [ ] Todos os arquivos necessários criados
- [ ] requirements.txt gerado
- [ ] .gitignore configurado adequadamente
- [ ] Documentação da tarefa preenchida
- [ ] Commit realizado com mensagem descritiva
- [ ] Pull Request aberto

---

## 🔧 Comandos Úteis para o Futuro

```bash
# Ativar ambiente virtual
poetry shell

# Instalar nova dependência
poetry add nome-do-pacote

# Instalar dependência de desenvolvimento
poetry add --group dev nome-do-pacote

# Atualizar requirements.txt
poetry export -f requirements.txt --output requirements.txt --without-hashes

# Executar o projeto
python run.py

# Executar testes (quando criarmos)
poetry run pytest

# Formatar código
poetry run black .

# Verificar qualidade do código
poetry run flake8
```

---

## 🆘 Precisa de Ajuda?

### Erros Comuns:

1. **"poetry: command not found"**
   - Reinicie o terminal após instalar o Poetry
   - Verifique se o Poetry foi adicionado ao PATH

2. **Erro de permissão no macOS/Linux**
   - Use `python3` em vez de `python`
   - Verifique se o Python está instalado corretamente

3. **Flask não encontrado**
   - Certifique-se de estar no ambiente virtual (`poetry shell`)
   - Execute `poetry install` novamente

4. **Página não carrega**
   - Verifique se não há erros no terminal
   - Confirme se está acessando `http://localhost:5000`

---

## 📚 Para Saber Mais

- [Documentação do Poetry](https://python-poetry.org/docs/)
- [Tutorial Flask](https://flask.palletsprojects.com/en/2.0.x/tutorial/)
- [Python Virtual Environments](https://docs.python.org/3/tutorial/venv.html)
- [Bootstrap 5 Documentation](https://getbootstrap.com/docs/5.1/getting-started/introduction/)

---

**Parabéns! 🎉 Você está criando seu primeiro sistema web com Python!**

Agora esta pasta se tornará o repositório principal do sistema que vocês desenvolverão juntos.