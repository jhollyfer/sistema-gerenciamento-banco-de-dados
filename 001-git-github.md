# Git para Iniciantes — Guia Direto e Prático
 
> Aula focada em **comandos do dia a dia** com **exemplos reais** de quem está começando a programar.
 
---
 
## 1. O que é Git?
 
**Git** é a ferramenta que **guarda as versões do seu projeto**.
 
Imagina que você está construindo uma API. Hoje ela tem 10 rotas, semana que vem 15, daqui a um mês 30. O Git guarda cada uma dessas "fotografias" do projeto pra você poder voltar pra qualquer momento.
 
### Por que usar?
 
- **Voltar no tempo** quando quebrar algo
- **Recuperar arquivos** deletados
- **Trabalhar em equipe** sem pisar no pé do colega
- **Backup** do código (via GitHub)
---
 
## 2. Conceitos em 1 minuto
 
| Termo | O que é | Exemplo |
|-------|---------|---------|
| **Commit** | Um ponto na história | "adicionei rota de login" |
| **Branch** | Uma linha do tempo | `main`, `feature/login` |
| **Stage** | Área de preparação | "vou commitar esses 3 arquivos" |
| **Repositório** | Seu projeto com Git | A pasta `.git` dentro do projeto |
| **Remote** | Repositório na nuvem | GitHub |
| **HEAD** | Onde você está agora | "estou no último commit da main" |
 
---
 
## 3. Configuração Inicial (faça uma vez só)
 
Antes de tudo, configure seu nome e email:
 
```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu@email.com"
```
 
> Esses dados aparecem nos seus commits.
 
Para verificar:
 
```bash
git config --list
```
 
---
 
## 4. Iniciando um Projeto
 
### Cenário: você criou um projeto novo
 
```bash
# Cria a pasta do projeto
mkdir minha-api
cd minha-api
 
# Inicia o Git
git init
```
 
### Cenário: você quer baixar um projeto existente
 
```bash
git clone https://github.com/usuario/projeto.git
cd projeto
```
 
> `git clone` baixa o projeto **e já configura o Git** — não precisa rodar `git init` depois.
 
---
 
## 5. O Ciclo Básico (você vai usar TODO DIA)
 
```
modificar → git add → git commit → git push
```
 
### Exemplo real: criando um endpoint
 
```bash
# 1. Você criou o arquivo src/routes/login.js no editor
 
# 2. Vê o que mudou
git status
 
# 3. Adiciona ao Stage
git add src/routes/login.js
 
# 4. Cria o commit
git commit -m "feat: adiciona rota de login"
 
# 5. Envia pro GitHub
git push
```
 
Pronto. Esse é o fluxo. Tudo que vem a seguir são **variações** disso.
 
---
 
## 6. Comando `git status` — Seu Melhor Amigo
 
**Sempre rode isso antes de qualquer ação.**
 
```bash
git status
```
 
Ele te diz:
- Em qual branch você está
- Quais arquivos foram modificados
- Quais estão no Stage
- Quais ainda não foram rastreados
---
 
## 7. Comando `git add` — Adicionando ao Stage
 
### Adicionar um arquivo específico
 
```bash
git add src/routes/login.js
```
 
### Adicionar uma pasta inteira
 
```bash
git add src/routes/
```
 
### Adicionar TUDO que mudou
 
```bash
git add .
```
 
> O `.` é o mais usado no dia a dia. Adiciona tudo que está modificado na pasta atual e subpastas.
 
### Tirei algo do Stage por engano?
 
```bash
git restore --staged arquivo.js
```
 
Ou (jeito antigo, ainda funciona):
 
```bash
git rm --cached arquivo.js
```
 
---
 
## 8. Comando `git commit` — Salvando a Versão
 
```bash
git commit -m "mensagem aqui"
```
 
### Boas mensagens (padrão Conventional Commits)
 
```bash
git commit -m "feat: adiciona autenticação JWT"
git commit -m "fix: corrige bug no cálculo do total"
git commit -m "docs: atualiza README"
git commit -m "refactor: simplifica função de login"
git commit -m "style: aplica prettier no projeto"
git commit -m "test: adiciona testes do useAuth"
git commit -m "chore: atualiza dependências"
```
 
### Esqueci de adicionar um arquivo no último commit?
 
```bash
git add arquivo-esquecido.js
git commit --amend --no-edit
```
 
> Isso adiciona o arquivo no commit anterior sem mudar a mensagem.
 
---
 
## 9. Comando `git log` — Vendo o Histórico
 
```bash
git log
```
 
### Versão mais limpa (recomendada)
 
```bash
git log --oneline
```
 
Saída:
```
a1b2c3d (HEAD -> main) feat: adiciona rota de login
e4f5g6h fix: corrige validação de email
i7j8k9l initial commit
```
 
### Sair da tela
 
Aperta `q`.
 
---
 
## 10. Branches — Linhas do Tempo Paralelas
 
**Por que usar branches?** Para criar coisas novas sem quebrar o que já funciona.
 
### Cenário típico
 
Você está numa equipe. A `main` tem o código que está em produção. Você precisa criar uma feature nova. **Não mexe na main!** Cria uma branch.
 
### Listar branches
 
```bash
git branch
```
 
Saída (a `*` mostra onde você está):
```
* main
  feature/login
  feature/cadastro
```
 
### Criar uma branch nova
 
```bash
git branch feature/login
```
 
> Isso só **cria**. Você ainda está na `main`.
 
### Mudar de branch
 
```bash
git checkout feature/login
```
 
### Atalho — criar e já mudar
 
```bash
git checkout -b feature/login
```
 
> 99% das vezes você vai usar esse atalho.
 
### Voltar pra main
 
```bash
git checkout main
```
 
### Deletar branch (depois que terminou e mesclou)
 
```bash
git branch -d feature/login
```
 
---
 
## 11. `git merge` — Juntando Branches
 
Você terminou a feature na branch `feature/login` e quer levar pra `main`:
 
```bash
# 1. Vai pra branch que vai RECEBER o código
git checkout main
 
# 2. Mescla a feature
git merge feature/login
 
# 3. Apaga a branch antiga
git branch -d feature/login
```
 
### Fluxo visual
 
```
main:        A───B───C────────M
                      \      /
feature/login:         D────E
```
 
O `M` é o commit de merge — junção das duas linhas do tempo.
 
---
 
## 12. Trabalhando com GitHub (Remoto)
 
### Conectar projeto local ao GitHub
 
```bash
git remote add origin https://github.com/seu-usuario/seu-repo.git
```
 
> `origin` é o **apelido** do repositório remoto. É padrão usar esse nome.
 
### Ver os remotes configurados
 
```bash
git remote -v
```
 
### Enviar para o GitHub
 
```bash
git push
```
 
### Primeira vez enviando uma branch nova
 
```bash
git push -u origin HEAD:nome-branch
```
 
> O `-u` (upstream) faz o Git "lembrar" da conexão. Depois disso, basta `git push`.
>
> `HEAD` significa "a branch atual em que estou".
 
**Exemplo prático:**
 
```bash
# Estou na branch feature/login pela primeira vez
git push -u origin HEAD:feature/login
 
# Próximas vezes, só:
git push
```
 
### Trazer mudanças do GitHub
 
```bash
git pull
```
 
### Pull de uma branch específica (sem rebase)
 
```bash
git pull origin nome-branch --no-rebase
```
 
> `--no-rebase` força um **merge** ao invés de rebase. Útil quando você não quer reorganizar os commits.
 
---
 
## 13. Cenários Reais do Dia a Dia
 
### 🎯 Cenário 1: Começando o dia
 
```bash
git checkout main
git pull
```
 
> Sempre puxa o que tem de novo na main antes de começar a trabalhar.
 
---
 
### 🎯 Cenário 2: Criando uma feature nova
 
```bash
# 1. Atualiza a main
git checkout main
git pull
 
# 2. Cria branch nova a partir da main
git checkout -b feature/dashboard
 
# 3. Trabalha no código...
# 4. Salva mudanças
git add .
git commit -m "feat: cria página de dashboard"
 
# 5. Envia pro GitHub (primeira vez)
git push -u origin HEAD:feature/dashboard
```
 
---
 
### 🎯 Cenário 3: Continuando uma feature
 
```bash
# 1. Modifica os arquivos no editor
 
# 2. Confere o que mudou
git status
 
# 3. Adiciona e commita
git add .
git commit -m "feat: adiciona gráfico de vendas"
 
# 4. Envia
git push
```
 
---
 
### 🎯 Cenário 4: Terminei a feature, quero levar pra main
 
```bash
# 1. Vai pra main e atualiza
git checkout main
git pull
 
# 2. Mescla a feature
git merge feature/dashboard
 
# 3. Envia a main atualizada
git push
 
# 4. Apaga a branch local
git branch -d feature/dashboard
```
 
> Em equipes sérias, esse passo é feito via **Pull Request** no GitHub.
 
---
 
### 🎯 Cenário 5: Quero ver como estava o código ontem
 
```bash
# 1. Pega o hash do commit
git log --oneline
 
# 2. Volta pra ele
git checkout a1b2c3d
 
# 3. Olha o que precisa olhar...
 
# 4. Volta pro presente
git checkout main
```
 
---
 
### 🎯 Cenário 6: Apaguei um arquivo sem querer
 
**Se ainda não commitou:**
```bash
git restore arquivo-perdido.js
```
 
**Se já commitou a deleção:**
```bash
# Acha o último commit onde o arquivo existia
git log --oneline
 
# Recupera ele
git checkout a1b2c3d -- arquivo-perdido.js
 
# Commita a recuperação
git commit -m "fix: recupera arquivo deletado por engano"
```
 
---
 
### 🎯 Cenário 7: Modifiquei e quero descartar tudo
 
```bash
# Descarta mudanças num arquivo específico
git restore arquivo.js
 
# Descarta TUDO que não foi commitado
git restore .
```
 
> ⚠️ Cuidado: isso **não dá pra desfazer**.
 
---
 
### 🎯 Cenário 8: Commitei e me arrependi (ainda não fiz push)
 
**Desfazer o último commit mantendo as mudanças:**
```bash
git reset --soft HEAD~1
```
 
**Desfazer o último commit e jogar fora as mudanças:**
```bash
git reset --hard HEAD~1
```
 
> ⚠️ `--hard` apaga seu trabalho. Use com atenção.
 
---
 
### 🎯 Cenário 9: Preciso pausar o trabalho sem commitar
 
```bash
# Guarda as mudanças num "bolso"
git stash
 
# Faz o que precisa fazer (trocar de branch, etc)
 
# Volta com as mudanças
git stash pop
```
 
> Útil quando precisa trocar de branch rápido pra resolver algo urgente.
 
---
 
### 🎯 Cenário 10: Ver as diferenças antes de commitar
 
```bash
# Ver o que mudou nos arquivos não-staged
git diff
 
# Ver o que está no Stage prestes a ser commitado
git diff --staged
```
 
---
 
## 14. `.gitignore` — Arquivos que NÃO Vão pro Git
 
Crie um arquivo `.gitignore` na raiz do projeto:
 
```gitignore
# Dependências
node_modules/
 
# Variáveis de ambiente
.env
.env.local
 
# Build
dist/
build/
 
# Editor
.vscode/
.idea/
 
# Sistema operacional
.DS_Store
Thumbs.db
 
# Logs
*.log
```
 
> **NUNCA** commite `node_modules`, `.env` ou arquivos de build. O `.gitignore` resolve isso.
 
---
 
## 15. Cheat Sheet Completo
 
### Configuração
```bash
git config --global user.name "Nome"
git config --global user.email "email"
git config --list
```
 
### Iniciando
```bash
git init                          # Inicia repo no projeto
git clone <url>                   # Baixa projeto do GitHub
```
 
### Ciclo básico
```bash
git status                        # Ver estado
git add .                         # Adiciona tudo ao Stage
git add arquivo                   # Adiciona arquivo
git add pasta/                    # Adiciona pasta
git commit -m "mensagem aqui"     # Cria commit
git log --oneline                 # Vê histórico
```
 
### Desfazendo
```bash
git restore arquivo               # Descarta modificação
git restore --staged arquivo      # Tira do Stage
git reset --soft HEAD~1           # Desfaz último commit (mantém código)
git reset --hard HEAD~1           # Desfaz último commit (apaga tudo)
git commit --amend --no-edit      # Adiciona ao último commit
```
 
### Branches
```bash
git branch                        # Lista branches
git branch nome-branch            # Cria branch
git checkout nome-branch          # Muda de branch
git checkout -b nome-branch       # Cria e já muda
git checkout hash-commit          # Vai pra um commit específico
git merge nome-branch             # Mescla branch na atual
git branch -d nome-branch         # Apaga branch
```
 
### GitHub
```bash
git remote add origin <url>       # Conecta ao GitHub
git remote -v                     # Lista remotes
git push                          # Envia commits
git pull                          # Traz commits
git push -u origin HEAD:nome-branch         # Primeira vez enviando branch
git pull origin nome-branch --no-rebase     # Pull forçando merge
```
 
### Extras úteis
```bash
git stash                         # Guarda mudanças temporariamente
git stash pop                     # Recupera mudanças guardadas
git diff                          # Ver mudanças
git diff --staged                 # Ver mudanças no Stage
```
 
---
 
## 16. Rotina Mental do Dev
 
### Começou o dia
```bash
git checkout main
git pull
```
 
### Vai mexer em algo novo
```bash
git checkout -b feature/o-que-vai-fazer
```
 
### A cada pedaço pronto
```bash
git add .
git commit -m "feat: descreve o que fez"
```
 
### Final do dia / pausou
```bash
git push
```
 
### Terminou a feature
```bash
git checkout main
git pull
git merge feature/o-que-fez
git push
```
 
---
 
## 🎯 Resumão Final
 
> **Git rastreia. GitHub guarda. Branches isolam. Commits salvam.**
>
> Você não precisa decorar tudo. Use o cheat sheet, repita o ciclo básico todo dia, e em 2 semanas vira automático. 🚀
 






