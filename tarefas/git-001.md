# 🚀 Projeto Git & Python - Bem-vindo!

Este projeto foi criado para ensinar desenvolvedores vindos do mundo COBOL a trabalhar com Git, GitHub, Python e o ecossistema web moderno.

## 📚 Sobre o Projeto

Aqui você aprenderá:
- Como usar Git e GitHub para versionamento de código
- Fundamentos da linguagem Python
- Como funciona o desenvolvimento web moderno
- Boas práticas de colaboração em projetos

## 🎯 Como Funcionam as Tarefas

Cada tarefa seguirá o padrão **Git-XXX**, onde XXX é o número da tarefa.

Para cada tarefa você deverá:
1. Criar uma nova branch específica para a tarefa
2. Documentar o que aprendeu em um arquivo específico
3. Fazer commit das suas alterações
4. Enviar para o GitHub
5. Abrir um Pull Request (PR)

---

## 📝 Git-001: Clonando o Projeto

### Objetivo
Aprender a clonar um repositório Git e fazer seu primeiro commit e Pull Request.

### O que você vai aprender
- Clonar um repositório remoto
- Criar uma nova branch
- Fazer commit de arquivos
- Enviar código para o GitHub
- Abrir um Pull Request

### Passo a Passo

#### 1. Clonar o Projeto

Você pode clonar este projeto de **3 formas diferentes**. Escolha a que preferir:

##### **Opção A: Git via linha de comando (Terminal)**

```bash
git clone git@github.com:saimonventura/git-python.git
cd git-python
```

##### **Opção B: GitHub Desktop**

1. Abra o GitHub Desktop
2. Clique em **File** → **Clone Repository**
3. Na aba **URL**, cole: `git@github.com:saimonventura/git-python.git`
4. Escolha onde salvar o projeto no seu computador
5. Clique em **Clone**

##### **Opção C: VS Code**

1. Abra o VS Code
2. Pressione `Cmd+Shift+P` (Mac) ou `Ctrl+Shift+P` (Windows/Linux)
3. Digite "Git: Clone" e pressione Enter
4. Cole a URL: `git@github.com:saimonventura/git-python.git`
5. Escolha uma pasta no seu computador
6. Clique em "Open" quando aparecer a notificação

---

#### 2. Criar uma Nova Branch

Depois de clonar o projeto, crie uma branch para sua tarefa:

```bash
git checkout -b git-001-meu-nome
```

💡 **Substitua "meu-nome"** pelo seu nome. Exemplo: `git-001-joao-silva`

Se estiver usando **GitHub Desktop**:
1. Clique em **Current Branch** no topo
2. Clique em **New Branch**
3. Digite o nome: `git-001-meu-nome`
4. Clique em **Create Branch**

---

#### 3. Criar seu Arquivo de Documentação

Crie um novo arquivo na pasta `tarefas/` com o nome: `git-001-meu-nome.md`

**Estrutura do arquivo:**

```markdown
# Git-001: Clonando o Projeto

## Nome
[Seu nome aqui]

## Data
[Data de conclusão]

## Como eu clonei o projeto

[Descreva aqui o método que você escolheu: linha de comando, GitHub Desktop ou VS Code]

## Passos que segui

1. [Primeiro passo que você fez]
2. [Segundo passo]
3. [E assim por diante...]

## Dificuldades encontradas

[Descreva qualquer dificuldade que teve, ou escreva "Nenhuma"]

## O que aprendi

[Escreva com suas palavras o que você aprendeu com esta tarefa]

## Comandos Git utilizados

```bash
# Liste aqui os comandos que você usou
# Exemplo:
# git clone git@github.com:saimonventura/git-python.git
# git checkout -b git-001-meu-nome
```
```

---

#### 4. Fazer Commit das Alterações

Depois de criar e preencher seu arquivo:

```bash
# Adicionar o arquivo ao staging
git add tarefas/git-001-meu-nome.md

# Fazer o commit
git commit -m "Git-001: Documentação de como clonei o projeto"
```

No **GitHub Desktop**:
1. Você verá seu arquivo na lista de "Changes"
2. Escreva uma mensagem de commit: "Git-001: Documentação de como clonei o projeto"
3. Clique em **Commit to git-001-meu-nome**

---

#### 5. Enviar para o GitHub

```bash
git push origin git-001-meu-nome
```

No **GitHub Desktop**:
1. Clique em **Push origin** no topo

---

#### 6. Abrir um Pull Request

1. Acesse: https://github.com/saimonventura/git-python
2. Você verá um banner amarelo sugerindo abrir um Pull Request
3. Clique em **Compare & pull request**
4. Preencha:
   - **Título**: `Git-001: [Seu Nome] - Clone e documentação`
   - **Descrição**: Resuma o que você fez e aprendeu
5. Clique em **Create pull request**

---

## ✅ Critérios de Conclusão

Sua tarefa Git-001 estará completa quando:

- [ ] Você clonou o repositório com sucesso
- [ ] Criou uma branch com o padrão correto (`git-001-seu-nome`)
- [ ] Criou o arquivo de documentação na pasta `tarefas/`
- [ ] Preencheu todas as seções do arquivo
- [ ] Fez commit das alterações
- [ ] Enviou a branch para o GitHub
- [ ] Abriu um Pull Request

---

## 🆘 Precisa de Ajuda?

Se encontrar dificuldades:

1. **Erros de permissão SSH**: Certifique-se de que configurou sua chave SSH no GitHub
   - Tutorial: https://docs.github.com/pt/authentication/connecting-to-github-with-ssh

2. **Não sabe usar o terminal**: Use o GitHub Desktop ou VS Code - são interfaces visuais mais amigáveis

3. **Dúvidas sobre Git**: Consulte a [documentação oficial do Git em português](https://git-scm.com/book/pt-br/v2)

---

## 📖 Próximas Tarefas

Após concluir o Git-001, você estará pronto para:
- Git-002: Fundamentos de Python
- Git-003: Trabalhando com branches e merge
- E muito mais!

---

## 🎓 Glossário

- **Repository (Repositório)**: Local onde o código do projeto fica armazenado
- **Clone**: Fazer uma cópia do repositório remoto para sua máquina
- **Branch**: Uma "linha do tempo" paralela onde você pode trabalhar sem afetar o código principal
- **Commit**: Salvar suas alterações com uma mensagem descritiva
- **Push**: Enviar seus commits locais para o GitHub
- **Pull Request (PR)**: Pedido para que seu código seja revisado e incorporado ao projeto principal
- **Origin**: Nome padrão do repositório remoto no GitHub

---

**Boa sorte e bons estudos! 🚀**
