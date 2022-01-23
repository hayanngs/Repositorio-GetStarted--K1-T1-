## Funcionamento do Git

**Working Directory (untracked ou não rastreado)**: É antes de adicionar a alteração ao 
controle de versão, são os arquivos **modificados**, **excluídos** ou **adicionados**.

Após o comando `git add` a alteração é adicionada ao **staged**.

**Staging Area (staged)**: São os arquivos preparados para serem versionados.

Os arquivos em **staged** já podem ser "commitados" pelo comando `git commit`.

**Committed**: São as alterações salvas

## Configurações do usuário
Seta o seu nome de usuário nas configurações global.
```
$ git config --global user.name "<nome>"
```

Seta seu e-mail nas configurações global.
```
$ git config --global user.email "<email>"
```

Lista as configurações global.
```
$ git config --global --list
```

Lista as configurações do repositório atual.
```
$ git config --list
```

## Criação de um repositório local

Inicializa um repositório local.
```
$ git init
```

## Versionamento - Adicionando alterações

Exibe o estado das alterações no repositório.
```
$ git status
```
Adiciona todos os arquivos ou um único arquivo específico.
```
$ git add .	
$ git add <nome do arquivo>	
```
> Nota: `-A`, `.` e `--all` têm a mesma função de se referir a todos.

## Versionamento - Salvando alterações

Salva alterações numa versão.
```
$ git commit
$ git commit -m "<descrição>"
$ git commit -a -m "Mensagem"
$ git commit --amend
```
> Nota: `-m` é um parâmetro usado para adicionar uma descrição ao commit.
> Nota: `-a` é o mesma função do `git add` já direto no commit.
> Nota: `--amend` inclui alterações que estão em staged ao último commit feito localmente

## Visualizar alterações
Mostra a diferença entre o repositório de trabalho e o último commit.
```
$ git diff
$ git diff --cached
$ git diff --staged
```
> Nota: `--cached` e `--staged` são sinônimos.

## Histórico de alterações
Exibe o log (histórico) das alterações de acordo com o parâmetro.
```
$ git log -n 
$ git log -p 
$ git log --stat 
$ git log --shortstat
$ git log --name-only
$ git log --name-status
$ git log --abbrev-commit 
$ git log --relative-date 
$ git log --graph
$ git log --oneline
```
> Nota: `-n` Listagem limitada a N commits. 
> Nota: `-p` Mostra as mudanças de cada arquivo de acordo com o commit. É como se fosse um `git diff` em cada commit. 
> Nota: `--stat` Mostra a quantidade de alterações em cada arquivo em formato visual, sem mostrar as mudanças específicas. 
> Nota: `--shortstat` Mostra somente a quantidade de alteração de forma menos visual que `--stat`. 
> Nota: `--name-only` Mostra a lista de arquivos modificados em cada commit. 
> Nota: `--name-status` Mostra a lista de arquivos modificados em cada commit e para cada arquivo mostra as letras M, A ou D. M - Arquivo modificado A - Arquivo adicionado D - Arquivo removido .
> Nota: `--abbrev-commit` Faz exatamente igual ao comando `git log`, porém mostra somente poucos caracteres do commit, ao invés de todos os 40.
> Nota: `--relative-date` Mostra os commits com a data relativa comparado a data do dia atual. Ao invés de mostrar a data em que foi feita, mostra quanto tempo atrás foi feito. Por exemplo, "8 semanas atrás", "2 dias atrás".
> Nota: `--graph` Mostra a lista de commits juntamente com alguns caracteres no início da linha que mostram quando uma branch surgiu e quando houve um merge. 
> Nota: `--oneline` Faz a listagem de commits mostrando o hash abreviado e a mensagem usada para o commit. Além disso, como o nome já diz, cada commit é mostrado em somente uma linha. 

Também é possível informar o seu próprio formato através do parâmetro `--pretty.:format`.
> Exemplo: `git log --pretty=format:"%h - %p: Feito por %an"` 
> Exemplo: `git log --pretty=format:"%h: %ar - (%ae) %an"` 

O comando `git log --oneline` pode ser escrito da seguinte maneira: `git log --pretty=format:"%h %s"`.

> `%H` Mostra o hash do commit. 
> `%h` Mostra o hash do commit abreviado. 
> `%P` Mostra o hash do commit anterior. 
> `%p` Mostra o hash do commit do commit anterior abreviado. 
> `%an` Mostra o nome do autor do commit. 
> `%ae` Mostra o e-mail do autor do commit. 
> `%ar` Mostra a data relativa ao dia de hoje. Há quanto tempo atrás a alteração foi feita. 
> `%s` Mostra o comentário realizado no commit. 



## Usando commits anteriores
Volta para o commit especificado no parâmetro com o hash.
```
git checkout <6 primeiros dígitos do hash do commit>
```
Volta para o "head" ou "master", que é a mais atualizada/recente.
```
$ git checkout master
```

## Desfazendo alterações
Desfaz alteração num arquivo já existente, não funciona em arquivos novos ou adicionados.
```
$ git checkout <arquivo especifico>
```
Volta os arquivos em Staged para Não rastreado e lista os arquivos commitados e alterados.
```
$ git reset
```
Da um rollback nas alterações feitas nos arquivos commitados e deleta os arquivos em Staged.
```
$ git reset --hard
```

## Desfazendo alterações não rastreadas
Limpa os arquivos não rastreados.
```
$ git clean
$ git clean -f
```
> Nota: `-f` force força a limpeza.



## Ignorando arquivos

Cria-se um arquivo **.gitignore**, nele é adicionado a cada linha o arquivo ou o tipo de arquivo que se deseja ignorar.

## Clonando repositório

```
$ git clone <diretório do repositório a ser clonado> <diretório destino>
```
## Criando branch local
Lista as branchs locais.
```
$ git branch
```
Cria uma branch local com o nome passado por parâmetro.
```
$ git branch <nome da branch>
```
Troca de branch para a branch de nome passado por parâmetro, se a branch não existir então ela apenas será criada mas não irá trocar de branch.
```
$ git checkout <nome da branch>
```
Cria uma branch nova e já faz o checkout(troca) dela.
```
$ git checkout -b <nome da branch>
```
## Enviando branch para repositório
```
$ git push --set-upstream origin <nome da branch mapeada no repositório remoto>
$ git push -u origin <nome da branch mapeada no repositório remoto>
```
> Nota: `-u` e `--set-upstream` são sinônimos.

## Atualizando branch
Busca e baixa conteúdo do repositório remoto e faz a atualização imediata ao repositório local para que os conteúdos sejam iguais.
```
$ git pull
```
> Nota: O `git pull` executa dois comandos, o `git fetch` e o `git merge`.

Baixa atualizações do repositório remoto para o local, porém não efetua o merge.
```
$ git fetch
```
## Fetch


## Remover branches locais
Remove uma branch local, `-D` força a remoção caso algo impeça.
```
$ git branch -d <nome da branch>
```

## Remover branches remotas
Remove uma branch do servidor remoto.
```
$ git push --delete origin <nome da branch no servidor remoto>
```

## Renomear branch local
Renomeia a branch na qual se está checado.
```
$ git branch -m <novo nome>
```
Renomeia uma branch não estando checado nela.
```
$ git branch -m <nome da branch a ser renomeada> <novo nome>
```
## Renomear branch remota
Não existe um comando específico, tem que apagar a do servidor e dar push de novo. 
1. `git pull` para trazer a branch atualizada
2. `git branch -m <novo nome>` para renomear a branch
3. `git push --delete <branch a ser renomeada>` para remover a branch do repositório remoto
4. `git push -u origin <novo nome>` push da branch renomeada para o repositório remoto

## Mesclando alterações
```
$ git merge <branch que vai mergear na atual>
```
> Nota: O git merge é preciso estar checado na branch que vai receber as mudanças que virão da branch passada por parâmetro.
> Nota: O git merge já faz o commit das alterações se não houver conflito.

## Resolvendo conflitos
O conflito é resolvido manualmente no arquivo onde está o conflito.

## Resolução de conflitos usando kdiff3
Aabre a ferramenta de merge.
```
$ git mergetool
```
Adicionando ferramenta de merge.
```
$ git config --global --add merge.tool kdiff3
```
Caminho para o diretório onde a ferramenta está instalada.
```
$ git config --global --add merge.tool.kdiff3.path
```
Configuração para o kdiff.
```
$ git config --global --add merge.tool.kdiff3.trustExitCode false
```

## Exemplo de SCM(Source Code Management
>tags: Marca a versão estável da master
branch master: É uma versão estável do sistema
branch develop: É criado a partir da master para desenvolver e testar features
branch features: É onde se desenvolve sem garantias de que estabilidade.


## Pull Request

É feito direto no github na hora de mergear uma branch com a master/main.

## Criação e listagem de tag
Tag é um ponteiro que marca algum commit específico.
Cria uma tag e adiciona descrição a ela.
```
$ git tag -a <nome da tag/versão da tag> -m "<descrição da tag>"
```
Cria uma tag de uma outra branch diferente da checada.
```
$ git tag -a <nome da tag/versão da tag> <código hash do commit>
```
Mostra a listagem das tags.
```
$ git tag
```

## Enviando tag para repositório
```
$ git push origin <nome da tag>
```
## Utilizando tags

Quando voltar numa tag no meio do histórico e fazer commit a partir 
dela, esses commits não ficarão rastreados, então é necessário criar 
uma branch a partir desse commit e depois trazer ele pro atual, 
pois se não ele irá se perder.*/


## Removendo tags local
```
$ git tag -d <nome da tag>
```
## Removendo tags remoto
```
$ git push --delete origin <nome da tag no remoto>
```
## Tag em commits antigos

Primeira maneira
1. Faz checkout no commit antigo
2. Cria a tag
3. Push da tag

Segunda maneira
1. Descrito na criação da tag

## Stash - Uso e criação
Guarda em memória as alterações atual que ainda não foram commitadas para que seja possível trocar de branch sem commitar ou ter que reverter as mudanças.
```
$ git stash
```
Cria um stash com descrição.
```
$ git stash save <"descrição">
```
Mostra a listagem dos stash em memória.
```
$ git stash list
```

## Stash - Listando e removendo
Aplica o primeiro stash à branch atual, porém o stash contina em memória.
```
$ git stash apply
```
Aplica o stash selecionado à branch atual, porém o stash contina em memória.
```
$ git stash apply <stash@{3}>
```
Aplica o primeiro stash a branch atual e o remove.
```
$ git stash pop
```
Aplica o stash selecionado a branch atual e o remove.
```
$ git stash pop <stash@{3}>
```
Remove o stash da memória.
```
$ git stash drop <stash@{3}>
```

## Desfazendo commits local
```
$ git reset --hard HEAD~<quantidade de commits>
```

**Free Software, Hell Yeah!**

