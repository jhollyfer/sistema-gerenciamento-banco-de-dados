# Atividades Práticas — Git
 
> 3 atividades progressivas pra fixar o conteúdo. Faça **na sequência** — cada uma constrói em cima da anterior.
 
---
 
## 📝 Atividade 1 — O Ciclo Básico (Iniciante)
 
**Objetivo:** Dominar o fluxo `init → add → commit` e navegar pelo histórico.
 
**Tempo estimado:** 20 minutos
 
### Passo a passo
 
**1. Crie a estrutura do projeto**
 
```bash
mkdir minha-loja
cd minha-loja
```
 
**2. Inicie o Git e configure (se ainda não fez)**
 
```bash
git init
git config --global user.name "Seu Nome"
git config --global user.email "seu@email.com"
```
 
**3. Crie um arquivo `produtos.txt`** com o conteúdo:
 
```
Camisa - R$ 50
Calça - R$ 100
Tênis - R$ 200
```
 
**4. Verifique o status**
 
```bash
git status
```
 
> Você deve ver `produtos.txt` como **untracked**.
 
**5. Faça o primeiro commit**
 
```bash
git add produtos.txt
git commit -m "feat: adiciona lista inicial de produtos"
```
 
**6. Adicione um produto novo** ao arquivo:
 
```
Camisa - R$ 50
Calça - R$ 100
Tênis - R$ 200
Boné - R$ 40
```
 
**7. Commite essa mudança**
 
```bash
git status
git add .
git commit -m "feat: adiciona boné na lista"
```
 
**8. Aumente o preço do tênis para R$ 250** e commite:
 
```bash
git add .
git commit -m "fix: atualiza preço do tênis"
```
 
**9. Veja todo o histórico**
 
```bash
git log --oneline
```
 
> Você deve ver 3 commits.
 
### ✅ Missão cumprida se:
 
- [ ] `git log --oneline` mostra 3 commits
- [ ] `git status` mostra "nothing to commit, working tree clean"
- [ ] Você consegue identificar o hash de cada commit
### 🎁 Desafio extra
 
Crie um arquivo `clientes.txt`, modifique-o **mas não commite**. Depois desfaça as mudanças com `git restore`.
 
---
 
## 📝 Atividade 2 — Branches e Merge (Intermediário)
 
**Objetivo:** Trabalhar com branches paralelas e mesclar mudanças.
 
**Tempo estimado:** 30 minutos
 
> Continue no projeto `minha-loja` da Atividade 1.
 
### Passo a passo
 
**1. Confira em qual branch você está**
 
```bash
git branch
```
 
> Você deve estar na `main`.
 
**2. Crie uma branch nova pra adicionar uma seção de promoções**
 
```bash
git checkout -b feature/promocoes
```
 
**3. Crie um arquivo `promocoes.txt`** com:
 
```
PROMOÇÕES DA SEMANA
- Camisa: 20% OFF
- Tênis: 15% OFF
```
 
**4. Commite**
 
```bash
git add .
git commit -m "feat: cria seção de promoções"
```
 
**5. Volte pra main e veja o que acontece**
 
```bash
git checkout main
ls
```
 
> O `promocoes.txt` **sumiu**! Isso é normal — ele só existe na branch `feature/promocoes`.
 
**6. Crie OUTRA branch a partir da main** pra mexer nos produtos:
 
```bash
git checkout -b feature/categorias
```
 
**7. Modifique o `produtos.txt` adicionando categorias:**
 
```
[ROUPAS]
Camisa - R$ 50
Calça - R$ 100
 
[CALÇADOS]
Tênis - R$ 250
 
[ACESSÓRIOS]
Boné - R$ 40
```
 
**8. Commite**
 
```bash
git add .
git commit -m "feat: organiza produtos por categoria"
```
 
**9. Veja todas as branches que você tem**
 
```bash
git branch
```
 
> Você deve ver 3: `main`, `feature/promocoes`, `feature/categorias`.
 
**10. Mescle a `feature/promocoes` na main**
 
```bash
git checkout main
git merge feature/promocoes
```
 
> Agora o `promocoes.txt` apareceu na main!
 
**11. Mescle também a `feature/categorias`**
 
```bash
git merge feature/categorias
```
 
**12. Apague as branches que já foram mescladas**
 
```bash
git branch -d feature/promocoes
git branch -d feature/categorias
```
 
**13. Confira o histórico final**
 
```bash
git log --oneline
git branch
```
 
### ✅ Missão cumprida se:
 
- [ ] Os arquivos `produtos.txt` (com categorias) e `promocoes.txt` estão na `main`
- [ ] Só existe a branch `main` agora
- [ ] O `git log --oneline` mostra commits das duas branches mescladas
### 🎁 Desafio extra
 
Volte para um commit antigo usando `git checkout <hash>`, olhe os arquivos como estavam, e depois volte com `git checkout main`.
 
---
 
## 📝 Atividade 3 — GitHub e Fluxo Real (Avançado)
 
**Objetivo:** Conectar com GitHub e simular um fluxo de trabalho real de equipe.
 
**Tempo estimado:** 40 minutos
 
**Pré-requisito:** ter conta no [GitHub](https://github.com).
 
### Passo a passo
 
**1. Crie um repositório no GitHub**
 
- Vá em [github.com/new](https://github.com/new)
- Nome: `minha-loja`
- **Não marque** "Initialize with README"
- Clique em "Create repository"
- Copie a URL HTTPS (ex: `https://github.com/seu-usuario/minha-loja.git`)
**2. Conecte seu projeto local ao GitHub**
 
```bash
git remote add origin https://github.com/seu-usuario/minha-loja.git
git remote -v
```
 
**3. Envie tudo pra nuvem**
 
```bash
git push -u origin main
```
 
> Atualize a página do GitHub. Seus arquivos devem estar lá. 🎉
 
**4. Crie um `.gitignore`** na raiz do projeto:
 
```gitignore
# Sistema
.DS_Store
Thumbs.db
 
# Editor
.vscode/
 
# Logs
*.log
```
 
**5. Commite e envie**
 
```bash
git add .gitignore
git commit -m "chore: adiciona gitignore"
git push
```
 
**6. Simule trabalhar em uma feature nova**
 
```bash
git checkout -b feature/estoque
```
 
**7. Crie um arquivo `estoque.txt`:**
 
```
Camisa - 50 unidades
Calça - 30 unidades
Tênis - 25 unidades
Boné - 100 unidades
```
 
**8. Commite e envie a branch nova pro GitHub**
 
```bash
git add .
git commit -m "feat: adiciona controle de estoque"
git push -u origin HEAD:feature/estoque
```
 
> Vá no GitHub e veja a branch nova lá.
 
**9. Continue trabalhando — atualize um valor no estoque** (ex: tênis = 30 unidades) e commite:
 
```bash
git add .
git commit -m "fix: atualiza estoque do tênis"
git push
```
 
> Agora basta `git push` (sem `-u origin HEAD:...`) porque a conexão já foi configurada.
 
**10. Simule um "esqueci de algo" — adicione mais um produto no estoque** e use `--amend`:
 
```bash
# Edita o arquivo adicionando "Mochila - 40 unidades"
git add .
git commit --amend --no-edit
```
 
**11. Faça o merge na main**
 
```bash
git checkout main
git merge feature/estoque
git push
```
 
**12. Apague a branch local e a remota**
 
```bash
git branch -d feature/estoque
git push origin --delete feature/estoque
```
 
### ✅ Missão cumprida se:
 
- [ ] O repositório no GitHub tem todos os arquivos
- [ ] Existe um `.gitignore` no projeto
- [ ] A `feature/estoque` foi criada, mesclada e apagada
- [ ] Só a branch `main` existe (local e remoto)
- [ ] O `git log --oneline` mostra todo o histórico
### 🎁 Desafio extra
 
1. Crie uma feature nova chamada `feature/desconto`
2. Modifique a `main` enquanto trabalha nessa feature (simule alguém da equipe)
3. Use `git stash` antes de trocar de branch
4. Recupere o trabalho com `git stash pop`
---
 
## 🏆 Desafio Final — Cenário Caótico
 
Depois de completar as 3 atividades, tente esse cenário "real":
 
```bash
# 1. Você está na main, modificou 2 arquivos, mas precisa
#    trocar de branch URGENTE pra resolver um bug
git stash
 
# 2. Vá pra branch principal e crie uma branch de hotfix
git checkout main
git checkout -b hotfix/bug-critico
 
# 3. "Resolva o bug" (modifique algum arquivo)
git add .
git commit -m "fix: corrige bug crítico"
git push -u origin HEAD:hotfix/bug-critico
 
# 4. Mescle na main
git checkout main
git merge hotfix/bug-critico
git push
 
# 5. Apague a branch
git branch -d hotfix/bug-critico
 
# 6. Volte pro seu trabalho anterior
git stash pop
```
 
Se você conseguiu fazer tudo isso sem travar... **parabéns, você tá pronto pro mundo real!** 🚀
 
---
 
## 💡 Dicas Finais
 
- **Erre à vontade** num projeto de teste. É assim que se aprende.
- **`git status` é seu melhor amigo** — sempre rode antes de qualquer ação.
- **Commits pequenos e frequentes** são melhores que commits gigantes.
- **Mensagens de commit claras** vão te salvar daqui a 6 meses.
- Quando travar, lembra: **quase nada é irreversível no Git**.
 






