+++
title = "CodeceptJS"
weight = 20
+++

## Breve descrição sobre CodeceptJS

O CodeceptJS é um framework de teste de aceitação e de sistema end-to-end para JavaScript. Ele é projetado para simplificar a escrita e execução de testes automatizados para aplicativos da web, especialmente para aplicativos baseados em navegadores.

Para acessar a pagina inicial click no [link](https://codecept.io/)

E vou utilizar a versão webdriverIO do codeceptjs, para acessar a doc click no [link](https://codecept.io/helpers/WebDriver/#webdriver)

## Pré requisitos
* Ter o node instalado
  * Utilizei a versão v20.11.0 do windows
  * Para baixar a versão click no [link](https://nodejs.org/dist/v20.11.0/)
 
## Passos da configuração
- [X] Primeiro passo executar o comando `npm init -y` para criar o arquivo package.json
- [x] Segundo passo executar o comando `npm i codeceptjs@3.5.12 -D` para instalar as dependências
- [x] Terceiro passo executar o comando `npm i webdriverio@8.32.0 -D` para instalar as dependências
- [x] Quarto passo executar o comando `npx codeceptjs init` para criar a configuração inicial
- [X] Quinto passo criando o primeiro cenário de teste fazer o login no sistema

Logo abaixo mais detalhes sobre a execução de cada passo.

### Primeiro passo executar o comando `npm init -y` para criar o arquivo package.json
* O comando `npm init -y` é uma forma abreviada e automatizada de iniciar um novo projeto Node.js e criar um arquivo package.json sem ter que responder a uma série de perguntas interativas.
 
  Aqui está o que cada parte do comando significa:
  * npm: O Node Package Manager, usado para instalar e gerenciar pacotes em projetos Node.js.
  * init: Comando para inicializar um novo projeto Node.js.
  * -y: Uma opção que significa "sim" ou "yes", que responde automaticamente a todas as perguntas com os valores padrão, sem a necessidade de entrada do usuário.
  ```
  npm init -y
  ```
* Assim que o arquivo `packge.json` foi criado eu abri o arquivo e alterei as seguintes informações:
  ```
  "author": "Sérgio Junior Schmitt",
  ```

### Segundo passo executar o comando `npm i codeceptjs@3.5.12 -D` para instalar as dependências
* O comando npm i codeceptjs@3.5.12 -D é usado para instalar o CodeceptJS na versão específica 3.5.12 como uma dependência de desenvolvimento em um projeto Node.js.
 
  Aqui está o que cada parte do comando significa:
  * npm: O Node Package Manager, usado para instalar e gerenciar pacotes em projetos Node.js.
  * i (ou install): Comando para instalar pacotes.
  * codeceptjs@3.5.12: O nome do pacote (CodeceptJS) seguido pela versão específica (3.5.12) que você deseja instalar.
  * -D (ou --save-dev): Opção para instalar o pacote como uma dependência de desenvolvimento, o que significa que ele será listado no arquivo package.json sob a chave devDependencies.

  Portanto, ao executar esse comando, o npm irá baixar e instalar o CodeceptJS na versão 3.5.12 no seu projeto, adicionando-o ao seu arquivo package.json como uma dependência de desenvolvimento. Isso é útil quando você está trabalhando em um projeto que utiliza o CodeceptJS para testes automatizados e deseja garantir que todas as pessoas que colaboram no projeto usem a mesma versão do CodeceptJS.

  Assim que terminou de fazer a instalação criei o arquivo `.gitignore ` e dentro deste arquivo coloquei o nome da pasta `node_modules` para sempre que eu for atualizar o projeto essa pasta não ir, pois ela é muito grande e não faz sentido ficar armazenado no git

### Terceiro passo executar o comando `npm i webdriverio@8.32.0 -D` para instalar as dependências  
* O comando npm i webdriverio@8.32.0 -D é utilizado para instalar o WebdriverIO na versão específica 8.32.0 como uma dependência de desenvolvimento em um projeto Node.js. Aqui está o que cada parte do comando significa:

  * npm: O Node Package Manager, utilizado para instalar e gerenciar pacotes em projetos Node.js.
  * i (ou install): Comando para instalar pacotes.
  * webdriverio@8.32.0: O nome do pacote (WebdriverIO) seguido pela versão específica (8.32.0) que você deseja instalar.
  * -D (ou --save-dev): Opção para instalar o pacote como uma dependência de desenvolvimento, o que significa que ele será listado no arquivo package.json sob a chave devDependencies.
 
### Quarto passo executar o comando `npx codeceptjs init` para criar a configuração inicial
  * Comando para iniciar as configurações básicas, com isso será feito alguns questionamentos `npx codeceptjs init` que irá criar a estrutura inicial do projeto de teste, segue as respostas utilizadas nesse projeto:
    * Do you plan to write tests in TypeScript?: `N`
    * Where are your tests located? (./*_test.js): `Enter`
    * What helpers do you want to use? (Use arrow keys): Selecionar o WebDriver `Enter`
    * Where should logs, screenshots, and reports to be stored? (./output): `Enter`
    * English (no localization): Selecionar pt-BR caso queira em Portuguese Brasil `Enter`
    * [WebDriver] Base url of site to be tested https://www.saucedemo.com/v1/ `Enter`
    * [WebDriver] Browser in which testing will be performed (chrome): `Enter`
    * Feature which is being tested (ex: account, login, etc): login `Enter`
    * Filename of a test (login_test.js): `Enter`
 
### Quinto passo criando o primeiro cenário de teste fazer o login no sistema

No arquivo `login_test.js` será adicionado o cenário de login usando a maneira mais simples do codeceptjs para fazer uma automação.


Assim que terminei de criar os cenários, executei o comando `npx codeceptjs run` para verificar se os testes foram executados sem problema.


Com isso verifiquei que foi criado a pasta `output`, esta é outra pasta que adiciono no arquivo `.gitignore`, pois não vejo necessidade de ser enviado essa pasta para o repositório do git


## Breve descrição dos comandos do codecept que foram utilizados
* Aqui vou fazer uma breve descrição do que cada comando que está sendo utilizado faz, para quem se interessar em aprofundar mais sobre cada comando procurar pelo mesmo na documentação oficial do webdriver que esta no [link](https://codecept.io/helpers/WebDriver/)
  
  * Esse comando tem a finalidade de navegar para uma determinada página da web durante a execução do teste.
  No exemplo fornecido, `EU.amOnPage('/')`, o parâmetro `('/')` indica que o teste está navegando para a raiz do site, ou seja, a página inicial, que foi configurado no arquivo `codecept.conf.js` no atributo `url`.
    ```
    Eu.amOnPage('/');
    ```
  * Usado para preencher um campo de entrada `(input)` com um valor específico. Este campo espera que sejam passado dois atributos, o primeiro é o mapeamento do campo da tela que será informado o texto, o segundo é o texto que será inserido nesse campo.
    ```
    Eu.fillField('//input[@id="user-name"]', 'standard_user');
    ```
  * Usado para clicar em um elemento específico da tela, com isso, este comando espera que seja passado apenas um atributo, o atributo que será clicado.
    ```
    Eu.click('//input[@id="login-button"]');
    ```
  * Usado para esperar que um elemento específico apareça na tela.
    ```
    Eu.waitForElement('//span[@class="title"]')
    ```
  * Usado para verificar se o texto fornecido está presente dentro do elemento especificado, com isso passamos dois parâmetros, o primeiro é o texto que esperamos que esteja aparecendo na tela, o segundo é o mapeamento do texto.
    ```
    Eu.seeTextEquals('Products','//span[@class="title"]')
    ```
