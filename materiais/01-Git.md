# Guia Completo de Git para Iniciantes — Tudo que Você Precisa Saber

---

## 1.1. Exemplo simples: Por que usar Git?

Imagine que você está desenvolvendo um site e, ao longo do tempo, faz várias alterações nos arquivos. Sem Git, você pode acabar criando várias cópias do mesmo arquivo para salvar diferentes versões, como:

```
index_v1.html
index_final.html
index_final_corrigido.html
```

Isso rapidamente se torna confuso e difícil de gerenciar. Com o Git, você pode salvar cada alteração como um "commit", que é como um ponto de restauração. Por exemplo:

1. Você cria o arquivo inicial e faz um commit: `git commit -m "Cria estrutura inicial do site"`.
2. Adiciona um cabeçalho e faz outro commit: `git commit -m "Adiciona cabeçalho ao site"`.
3. Corrige um erro no cabeçalho e faz mais um commit: `git commit -m "Corrige erro no cabeçalho"`.

Agora, você tem um histórico claro de todas as mudanças feitas, e pode voltar a qualquer ponto no tempo, se necessário.

---

## 1.2. O que é versionamento de código?

Versionamento de código é o processo de registrar e gerenciar as alterações feitas em arquivos de um projeto ao longo do tempo. Ele permite:

* **Rastrear mudanças:** Saber quem fez o quê e quando.
* **Reverter alterações:** Voltar a uma versão anterior se algo der errado.
* **Colaborar:** Trabalhar com outras pessoas sem sobrescrever o trabalho delas.

O Git é uma ferramenta poderosa para implementar esse versionamento de forma eficiente e organizada.

---

## 3. Instalando o Git

### Windows

* Baixe o instalador em [git-scm.com](https://git-scm.com/download/win).
* Siga o assistente de instalação (pode deixar as configurações padrão).
* Após instalar, abra o **Git Bash** para usar comandos Git.

### macOS

* Você pode instalar pelo Homebrew (se tiver instalado):

```bash
brew install git
```

* Ou baixe direto de [git-scm.com](https://git-scm.com/download/mac).

### Linux

* Use o gerenciador de pacotes da sua distribuição, por exemplo, no Ubuntu/Debian:

```bash
sudo apt update
sudo apt install git
```

### Verificar instalação

Abra o terminal (Prompt de comando, PowerShell, Terminal, etc.) e digite:

```bash
git --version
```

Deve aparecer a versão do Git instalada.

---

## 4. Configuração inicial

Configure seu nome e email, que serão usados para identificar quem fez cada mudança (commit):

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu.email@exemplo.com"
```

Você pode checar as configurações com:

```bash
git config --list
```

Se você escrever seu nome ou email errado, ou estiver compartilhando o Git com outra pessoa, pode corrigir ou apagar as configurações usando:

```bash
git config --global --unset user.name
git config --global --unset user.email
```

Depois, configure novamente com os valores corretos.


---

## 5. Como iniciar um projeto com Git (repositório local)

1. **Entre na pasta do seu projeto:**

```bash
cd /caminho/para/seu/projeto
```

2. **Inicialize o repositório Git:**

```bash
git init
```

Isso cria uma pasta `.git` que armazena o histórico.

---

## 6. Ciclo básico do Git: status → add → commit

### a) Verificar o status dos arquivos

Veja quais arquivos foram alterados, quais estão prontos para o commit, etc:

```bash
git status
```

### b) Adicionar arquivos para o commit (staging)

Você precisa informar ao Git quais arquivos serão incluídos no próximo commit:

* Para adicionar um arquivo específico:

```bash
git add arquivo.txt
```

* Para adicionar todos os arquivos modificados e novos:

```bash
git add .
```

### c) Fazer um commit (salvar as mudanças)

```bash
git commit -m "Mensagem explicativa do que você fez"
```

Exemplo:

```bash
git commit -m "Adiciona função de login"
```

---

## 7. Visualizando o histórico

Para ver o histórico de commits:

```bash
git log
```

A saída mostra:

* ID do commit (hash)
* Autor
* Data
* Mensagem do commit

Para sair do `git log`, aperte `q`.

---

## 8. Visualizando mudanças antes do commit

Para comparar as mudanças feitas com a última versão salva:

```bash
git diff
```

Para ver as diferenças de um arquivo específico:

```bash
git diff arquivo.txt
```

---
### Avançando no git...


## 9. Desfazendo mudanças

* Descartar mudanças em arquivos modificados (voltar ao último commit):

```bash
git checkout -- arquivo.txt
```

* Remover um arquivo do staging (sem apagar o arquivo):

```bash
git reset HEAD arquivo.txt
```

---

## 10. Repositórios remotos

Repositórios remotos são cópias do seu projeto armazenadas na internet (GitHub, GitLab, Bitbucket, etc.). Eles permitem que você faça backup, trabalhe em equipe e compartilhe seu código.

Para entender melhor, veja o material [02-GitHub.md](./02-GitHub.md).

### a) Clonar um repositório remoto

Para copiar um projeto já existente para seu computador:

```bash
git clone https://url-do-repositorio.git
```

---

### b) Conectar seu repositório local a um remoto

Se você criou um projeto local e quer enviar para o GitHub, por exemplo:

```bash
git remote add origin https://github.com/usuario/repositorio.git
```

---

### c) Enviar mudanças para o remoto (push)

Envie seus commits para o servidor:

```bash
git push origin main
```

---

### d) Atualizar seu projeto local com mudanças do remoto (pull)

Baixe e integre alterações feitas por outras pessoas:

```bash
git pull origin main
```

---

## 11. Trabalhando com branches (ramificações)

Branches são usadas para desenvolver funcionalidades separadamente, sem afetar a branch principal (`main` ou `master`).

* Listar branches:

```bash
git branch
```

* Criar e mudar para uma nova branch:

```bash
git checkout -b minha-feature
```

* Mudar para outra branch:

```bash
git checkout main
```

* Unir (merge) uma branch com a branch atual:

```bash
git merge minha-feature
```



---

## 12. Comandos essenciais resumidos

| Comando                       | Descrição                                        | Exemplo                                                     |
| ----------------------------- | ------------------------------------------------ | ----------------------------------------------------------- |
| `git init`                    | Inicializa um repositório Git local              | `git init`                                                  |
| `git status`                  | Mostra status dos arquivos                       | `git status`                                                |
| `git add <arquivo>`           | Adiciona arquivo(s) ao staging                   | `git add README.md` / `git add .`                           |
| `git commit -m "mensagem"`    | Salva mudanças com mensagem                      | `git commit -m "Corrige bug"`                               |
| `git log`                     | Exibe histórico de commits                       | `git log`                                                   |
| `git diff`                    | Mostra diferenças entre versões                  | `git diff`                                                  |
| `git branch`                  | Lista branches                                   | `git branch`                                                |
| `git checkout <branch>`       | Muda para uma branch                             | `git checkout main`                                         |
| `git checkout -b <branch>`    | Cria e muda para uma nova branch                 | `git checkout -b feature-login`                             |
| `git merge <branch>`          | Mescla uma branch na branch atual                | `git merge feature-login`                                   |
| `git clone <url>`             | Clona um repositório remoto                      | `git clone https://github.com/usuario/repo.git`             |
| `git remote add origin <url>` | Conecta seu repo local a um remoto               | `git remote add origin https://github.com/usuario/repo.git` |
| `git push origin <branch>`    | Envia commits para repositório remoto            | `git push origin main`                                      |
| `git pull origin <branch>`    | Atualiza repositório local com o remoto          | `git pull origin main`                                      |
| `git checkout -- <arquivo>`   | Desfaz alterações não commitadas em arquivo      | `git checkout -- arquivo.txt`                               |
| `git reset HEAD <arquivo>`    | Remove arquivo do staging (sem apagar o arquivo) | `git reset HEAD arquivo.txt`                                |

---

## 13. Fluxo básico resumido

```bash
# Inicializar repositório
git init

# Adicionar arquivo ao staging
git add arquivo.txt

# Fazer commit
git commit -m "Mensagem"

# Conectar ao remoto (se houver)
git remote add origin https://...

# Enviar mudanças para o remoto
git push origin main

# Atualizar projeto local com mudanças do remoto
git pull origin main
```

---

## 14. Dicas finais

* Faça commits pequenos e com mensagens claras.
* Use branches para trabalhar em funcionalidades diferentes.
* Sempre puxe as últimas mudanças (`git pull`) antes de começar a trabalhar para evitar conflitos.
* Se der conflito de merge, aprenda a resolver manualmente.

---

## 15. Recursos adicionais

Se você quiser explorar mais sobre Git e GitHub, aqui estão alguns links úteis:

* [Recursos de Git e GitHub deste tutorial](./Recursos-adicionais.md)
