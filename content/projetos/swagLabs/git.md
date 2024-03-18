+++
title = "Git"
weight = 10
+++

## Segue uma breve descrição do git.
O Git é um sistema de controle de versão distribuído, amplamente utilizado para rastrear as mudanças no código-fonte durante o desenvolvimento de software. Ele foi criado por Linus Torvalds em 2005, inicialmente para o desenvolvimento do kernel do Linux, e desde então se tornou uma ferramenta essencial para desenvolvedores em todo o mundo.

Em termos simples, o Git permite que várias pessoas trabalhem simultaneamente no mesmo projeto, mantendo o controle de todas as alterações feitas ao código. Ele registra o histórico de alterações, possibilitando a reversão para versões anteriores do código, a criação de branches para desenvolvimento paralelo, a fusão de código entre diferentes branches e muito mais.

Para acessar a documentação oficial dos comandos click no [link](https://docs.gitlab.com/ee/gitlab-basics/start-using-git.html) 

## Comandos que serão utilizados no projeto

* O comando `git clone` é usado para criar uma cópia local de um repositório Git existente. Ele baixa todos os arquivos do repositório remoto para o seu computador e configura automaticamente o controle de versão Git, permitindo que você comece a trabalhar com o código imediatamente. Aqui está a sintaxe básica do comando:

    ```
    git clone <url do repositório a ser baixado>
    ```
* O comando `git init` é utilizado para criar um novo repositório Git em um diretório local. Quando você executa esse comando em um diretório, ele inicializa um novo repositório Git nesse diretório, permitindo que você comece a controlar as versões dos arquivos dentro dele. Aqui está a sintaxe básica do comando:
    ```
    cd meu-projeto
    git init
    ```
* O comando `git status` é usado para verificar o status atual do seu repositório Git. Ele mostra informações sobre quais arquivos foram modificados, quais estão sendo rastreados, quais não estão sendo rastreados e em qual branch você está. Aqui está a sintaxe básica do comando:
    ```
    git status
    ```
* O comando `git add` é usado para adicionar arquivos ao índice (também conhecido como área de preparação) do Git. Isso significa que você está preparando esses arquivos para serem incluídos no próximo commit. Existem algumas maneiras diferentes de usar o comando git add, dependendo de quais arquivos você deseja adicionar. Aqui esta uma das formas comuns de usar `git add`, esta forma adiciona todos os arquivos modificados e os novos:
    ```
    git add .
    ```
* O comando `git commit` é usado para criar um novo commit no repositório Git. Um commit é uma confirmação de uma alteração específica ou conjunto de alterações no seu projeto. O `-m` é uma opção para adicionar uma mensagem ao commit diretamente na linha de comando. Aqui está a sintaxe do comando:
    ```
    git commit -m "texto descritivo do commit"
    ```
* O comando `git push` é usado para enviar (ou "empurrar") os commits locais de uma branch para um repositório remoto. Isso sincroniza as alterações feitas localmente com o repositório remoto, permitindo que outros colaboradores vejam e acessem essas alterações. Aqui está a sintaxe básica do comando:
    ```
    git push
    ```
* O comando `git pull` é utilizado para atualizar o seu repositório local com as alterações do repositório remoto. Essencialmente, ele combina dois comandos: git fetch, que busca as atualizações do repositório remoto, e git merge, que mescla essas alterações com a sua branch local.
    ```
    git pull
    ```
* O comando `git tag` é utilizado para criar, listar, deletar ou verificar tags no repositório Git. As tags são uma forma de marcar commits específicos em um repositório Git como versões específicas ou pontos de interesse, facilitando a referência a eles no futuro. Aqui esta uma da forma de utilizar este comando:
    ```
    git tag <nome da tag>
    ```
* O comando `git push origin --tags` é usado para enviar (ou "empurrar") todas as tags locais que você criou para o repositório remoto chamado "origin". Este comando sincroniza as tags locais com o repositório remoto, permitindo que outras pessoas ou sistemas acessem essas tags.
Aqui está a explicação dos elementos no comando:

  * git push: Este é o comando para enviar alterações do seu repositório local para um repositório remoto.
  * origin: Este é o nome do repositório remoto. Geralmente, "origin" é o nome padrão atribuído ao repositório remoto quando você clona um repositório.
  * --tags: Esta é a opção que especifica que todas as tags locais devem ser empurradas para o repositório remoto.
    ```
    git push origin --tags
    ```
