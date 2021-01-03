# Git e GitHub

---

### Anotações

---

> Git foi criado em 2005, por Linus Torvalds
>
> GitHub surgiu em 2008

#### Configuração básica

```
$ git config --global user.name "seuNome"
$ git config --global user.email seuEmail 
```

#### Criar um repositório local

```
$ git init
```

#### Situação do arquivo

```
$ git status
```

#### Deixar o arquivo rastreado

```
git add nomeDoArquivo
git add . //para adicionar todos os arquivos
```

#### Ignorar arquivos

Criar um arquivo **.gitignore** com os nomes dos arquivos que não deseja rastrear

Caso queira selecionar por extensão... ***.extensão** dentro do arquivo

#### Gravar arquivo no repositório

```
git commit -m "descricaoDaVersao" //apenas comita
git commit -am "descriçãoDaVersao" // rastreia mudanças e comita
```

#### Histórico das versões

```
$ git log //todos os commits
$ git log -n 2 //apenas os 2 ultimos commits
$ git log --oneline // resumo dos commits
$ git log --stat // resumo com número de linhas adicionadas ou removidas
$ git log -n 2 --online --stat // combinação dos comandos
```

#### Mudanças

```
$ git diff // somente para arquivos já rastreados
$ git diff --staged //mostra a diferença entre os arquivos na área de staged
$ git checkout -- nomeDoArquivo // retorna o arquivo **não rastreado** a versão anterior
$ git reset -- nomeDoArquivo // retorna o arquivo **já rastreado** a versão anterior
$ git reset --har // retira *todos* os arquivos do stage e retorna para o ultimo commit
$ git revert --no-edit códigoDoCommitt //desfazer as alterações do repositório
```

#### Remover arquivos

```
$ git rm nomeDoArquivo //remove do stage
```

#### Movendo e renomeando arquivos

```
$ git mv nomeArquivoOld nomeArquivoNew
```

#### Repositório Remoto

```
$ git init --bare nomeDoRepositorio
$ git remote /listar os repositórios adicionados
$ git remote -v //listar os repositórios adicionados e seus determinados url
$ git remote rename nomeServidorOld nomeServidorNew
$ git remote set-url //alterar o url do servidor
```

##### Servidor Local

```
$ git remote add servidor
file://192.168.1.1/opt/repositorios/nomeDorepositório //esse caminho é apresentado no comando anterior
```

##### Enviar Commits para o servidor

```
$ git push servidor master
$ git clione file:urlDoServidor // para obter cópia do repositório do servidor Git
$ git pull servidor master //sincronização do repositório local com o servidor
```

#### Branch

```
$ git branch //listar os branchs
$ git branch -v //listar os branchs associados aos commits realizados
$ git log --parentes //ver os commits e seus respectivos pais
$ git log --decorate //ver para qual commit o branch está apontando
$ git log --oneline --decorate --parents //exibe historico resumido dos commit qual apontamento e qual o pai
$ git branch nomeDoBranch //criar um novo Branch
$ git checkout nomeDoBranch //trocar de Branch
$ git checkout -b nomeDoBranch //criar e já mudar para o novo Branch
$ git branch -d nomeDoBranch //deletar um Branch **não tenha realizado commit**
$ git branch -D nomeDoBranch //deletar um Brach **Que já tenha realizado commit**
$ git branch --no-merged //verificar as Branches não mescladas
$ git branch --merged //verifica as Branches mescladas
$ git merge nomeDaBranchNaoMesclada -m "descriçao do commit"
$ git rebase nomedaBranchNaoMesclada //realiza o historico de commits **linearizado**
$ git branch -r //listar as Branches remotas
$ git branch -a //listar as Branhes locais e remotas
$ git branch -r -v //listar os commits que as Branches remotas estão apontando
$ git push origin nomeDaBranchQueQuerCompartilhar //Compartilhar os commits das Branches
$ git checkout -b origin/NomeDaBranchQueQuerImportar //criação de uma Branch local através de uma Branch remota, também chamadas de **Traking Branch**
$ git checkout -t origin/nomeDaBranchQueQuerImportar /outra forma de criar uma traking Branch
$ git fetch origin //trazer commits de um repositório remoto
$ git pull //obter commits e mesclar de uma vez só...seria um fetch seguido de um merge
$ git pull --rebase //commits linearizados...seria um fetch seguido de um rebase
$ git push origin :nomeDaBranchQueQuerDeletar

```

#### Tags

```
$ git tag v1.0 //criar ums tag
$ git tag //listar as tags
$ git tag banners codigoDoCommit //criar uma tag em um commite do passado
$ git tag -d nomeDaTagQueQuerDeletar //deleta uma tag
$ git tag -a v1.0 -m "descrição da tag" //criar tags mais detalhadas
$ git show -s v1.0 //exibe as informações anotadas da tag
$ git push origin v1.0 //compartilhar as tags no repositório remoto do GitHub
$ git push origin --tags //enviar todas as tags de uma única vez

```



## GitHub

#### Apontar o projeto para o GitHub

Após criado o repoditório no GitHub, dentro do repositório local, executar o comando gerado pelo repositório online:

```
git remote add origin https:github.com//...
```

Para enviar os arquivos para o GitHub execute o comando:

```
$ git push origin master
```

#### Obter códigos do GitHub

```
git clone https://github.com/...
```

#### Colaboração em projetos open source

**Fork** no GitHub //Para criar um repositório em sua conta

```
$ git clone https://...  //para clonar o repositório
```

 Após realizadas as alterações e commit realizar um **Pull request** no GitHub solicitando a alteração ao proprietário do projeto

#### Boas práticas

Utilizar um repositório central remoto

![](/home/celio/.config/Typora/typora-user-images/image-20210103114232086.png)

```
$ git clone https://...  //para realizar uma cópia local
$ git add . //para rastrear as alterações
$ git commit -m "descrição do commit" //para comitar as alterações
$ git push origin master //para compartilhar as alterações no repositório remoto
$ git pull --rebase origin master //para os demais obter os novos commits

//se surgir conflitos:
$ git add. 
$ git rebase --continue

//quando for fazer as entregas versionadas
$ git tag v1.0
$ git push origin --tags
```

###### Branches

Utilizar branches master, desenv, release, hotfix

> Referências:
>
> Aquiles, Alexandre; Ferreira, Rodrigo. Controle de versões com Git e Github. Casa do Código. São Paulo.