# Comandos e Exemplos por Aula — Git

> Extração de todos os comandos e exemplos práticos utilizados em cada aula.

---

## Como Funciona o Git

**Tipo:** Conceitual (sem comandos práticos)

### Conceitos apresentados
- **Commit** → ponto na história
- **Branch** → linha do tempo (a principal: `main`)
- **Stage Area** → área de preparação antes do commit
- **Repository (local)** → Git no projeto da sua máquina
- **Remote Repository** → repositório na nuvem (ex: GitHub)

### Exemplos usados
- Versões de um botão (azul → verde → vermelho) representando versões do projeto
- Analogia com o **Doctor Strange** manipulando a linha do tempo
- Caso do **Instagram + Reels** → branch alternativa para nova feature antes de mesclar na principal

---

## Comandos Básicos Para Repositório Local

**Tipo:** Apresentação dos comandos fundamentais

### Comandos apresentados

```bash
git init
```
Inicia o repositório do projeto.

```bash
git status
```
Verifica alterações em pastas e arquivos.

```bash
git add .
```
Adiciona todos os arquivos modificados ao Stage Area.

```bash
git add <arquivo>
```
Adiciona apenas um arquivo ou pasta ao Stage Area.

```bash
git commit -m "message here"
```
Cria um ponto na história com uma mensagem (até ~50 caracteres).

```bash
git log
```
Mostra todos os commits do projeto.

---

## Iniciando Um Repositório Git

**Tipo:** Prática inicial — primeira execução do Git

### Comandos usados

```bash
cd <caminho-da-pasta>
```
Navega até a pasta do projeto (change directory).

```bash
pwd
```
Mostra o caminho atual (print working directory).

```bash
git init
```
Inicia o repositório Git na pasta atual.

### Exemplos práticos da aula

**Pasta usada:** `git-aula`
**Arquivo dentro:** `frases.txt`

**Caminhos exemplificados:**
- Windows → `C:/git-aula`
- Mac/Unix → `/Users/Maik Brito/Desktop/git-aula`

**Resultado do `pwd` (Mac do instrutor):**
```
/Users/Maik Brito/Desktop/git-aula
```

**Dica do Mac:** arrastar a pasta direto para o terminal preenche o caminho.

---

## Adicionando Modificações ao Stage Area

**Tipo:** Prática — manipulação do Stage

### Comandos usados

```bash
git status
```
Mostra arquivos modificados, deletados, criados.

```bash
git add frases.txt
```
Adiciona arquivo específico ao Stage Area.

```bash
git add .
```
Adiciona todos os arquivos modificados ao Stage Area.

```bash
git rm --cached <arquivo>
```
Remove o arquivo do Stage Area (unstage), volta ao estado "não rastreado".

### Exemplos práticos da aula

**Arquivos manipulados:**
- `frases.txt` → adicionado ao Stage
- `.DS_Store` → arquivo oculto do Mac, removido do Stage com `git rm --cached`

**Mensagens de retorno do `git status`:**

Antes do `git add`:
```
On branch main
No commits yet
Untracked files:
  frases.txt
```

Depois do `git add frases.txt`:
```
On branch main
No commits yet
Changes to be committed:
  new file: frases.txt
```

Após adicionar tudo com `git add .` e remover o `.DS_Store`:
```bash
git rm --cached .DS_Store
```

---

## Criando o Primeiro Commit

**Tipo:** Prática — primeiro commit

### Comandos usados

```bash
git status
```
Verifica o estado antes do commit.

```bash
git restore <arquivo>
```
Restaura o arquivo para o último estado salvo no Stage Area.

```bash
git commit -m "initial commit"
```
Cria o primeiro commit do projeto.

### Exemplos práticos da aula

**Comando exato do primeiro commit:**
```bash
git commit -m "initial commit"
```

**Restauração demonstrada:**
```bash
git restore frases.txt
```
(removeu duas linhas que tinham sido adicionadas após o `git add`)

**Retorno do Git após o commit:**
```
[main (root-commit) abc1234] initial commit
 1 file changed, 5 insertions(+)
 create mode 100644 frases.txt
```

> **5 inserções** = 5 linhas do arquivo `frases.txt`

---

## Alterando e Commitando

**Tipo:** Prática — segundo commit (fluxo recorrente)

### Comandos usados

```bash
git status
```
Após modificar o arquivo.

```bash
git add frases.txt
```
Adiciona apenas o arquivo desejado (ignorando outros como `.DS_Store`).

```bash
git commit -m "adicionei novas linhas"
```
Cria o novo commit.

### Exemplos práticos da aula

**Comando exato do segundo commit:**
```bash
git commit -m "adicionei novas linhas"
```

**Retorno do Git:**
```
[main xyz5678] adicionei novas linhas
 1 file changed, 4 insertions(+), 1 deletion(-)
```

> **4 inserções** + **1 deleção** mostradas pelo Git

### Sacada apresentada
Depois do primeiro commit, o Git **rastreia automaticamente** o arquivo. Qualquer modificação aparece em `git status` sem precisar avisar de novo.

---

## Navegando Pelos Commits

**Tipo:** Prática — viagem no tempo

### Comandos usados

```bash
git log
```
Lista todos os commits, mostrando ID, autor, data, mensagem e onde está o `HEAD`.

```bash
:q
```
(ou `Ctrl+C`) — sai da tela do `git log`.

```bash
git checkout <hash-do-commit>
```
Navega até um commit específico (entra em **detached HEAD**).

```bash
git checkout main
```
Volta para a branch principal.

### Exemplos práticos da aula

**Saída do `git log` mostrando `HEAD → main`:**
```
commit xyz5678 (HEAD -> main)
Author: Maik Brito
    adicionei novas linhas

commit abc1234
Author: Maik Brito
    initial commit
```

**Navegação para o primeiro commit (usando início do hash):**
```bash
git checkout abc1234
```

**Mensagem do Git ao entrar em detached HEAD:**
```
You are in 'detached HEAD' state.
You can look around, make experimental changes...
```

**Retorno para o presente:**
```bash
git checkout main
```

### Conceitos vistos
- **HEAD** → ponteiro indicando onde você está
- **SHA-1** → algoritmo que gera o hash único de cada commit
- **Detached HEAD** → estado de "navegação" no passado
- Usar **só o início do hash** já é suficiente para o checkout

---

## Recuperando Um Arquivo Deletado

**Tipo:** Prática — resgate de arquivo

### Comandos usados

```bash
git status
```
Mostra a deleção rastreada.

```bash
git add frases.txt
```
Adiciona a deleção ao Stage Area.

```bash
git commit -m "deletado frases.txt"
```
Commita a deleção.

```bash
git log
```
Para encontrar o hash do commit onde o arquivo ainda existia.

```bash
git checkout <hash> -- frases.txt
```
Recupera o arquivo daquela versão específica.

```bash
git rm --cached frases.txt
```
Remove o arquivo recuperado do Stage Area (caso só tenha sido recuperado para visualizar).

```bash
git commit -m "resgatando frases.txt"
```
Commita a recuperação.

```bash
git restore frases.txt
```
Atalho para o caso em que o arquivo foi deletado mas **ainda não foi commitado**.

### Exemplos práticos da aula

**Fluxo completo demonstrado:**

```bash
# 1. Deletou o frases.txt manualmente

# 2. Adicionou a deleção ao Stage
git add frases.txt

# 3. Commitou a deleção
git commit -m "deletado frases.txt"

# 4. Pegou o hash do commit antigo (no git log)
git log

# 5. Recuperou o arquivo daquele commit
git checkout abc1234 -- frases.txt

# 6. Commitou a recuperação
git commit -m "resgatando frases.txt"
```

**Caso simples (sem commit de deleção):**
```bash
git restore frases.txt
```

---

## 📋 Cheat Sheet Consolidado

| Comando | Aula | Função |
|---------|------|--------|
| `cd <pasta>` | 3 | Navegar até a pasta |
| `pwd` | 3 | Ver o caminho atual |
| `git init` | 2, 3 | Iniciar repositório |
| `git status` | 2, 4, 5, 6, 8 | Ver alterações |
| `git add <arquivo>` | 2, 4, 6, 8 | Adicionar arquivo ao Stage |
| `git add .` | 2, 4 | Adicionar tudo ao Stage |
| `git rm --cached <arquivo>` | 4, 8 | Tirar do Stage |
| `git restore <arquivo>` | 5, 8 | Desfazer modificação |
| `git commit -m "msg"` | 2, 5, 6, 8 | Criar commit |
| `git log` | 2, 7, 8 | Ver histórico |
| `git checkout <hash>` | 7 | Voltar a um commit |
| `git checkout main` | 7 | Voltar à branch principal |
| `git checkout <hash> -- <arquivo>` | 8 | Recuperar arquivo de um commit |
| `:q` ou `Ctrl+C` | 7 | Sair da tela do `git log` |