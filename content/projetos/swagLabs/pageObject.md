+++
title = " "
linktitle = "Page Object"
weight = 40
+++

# Page Object

Page Object é um padrão de design de automação de testes de software usado principalmente em testes de interface do usuário (UI). Ele é utilizado para criar uma abstração da página web ou da interface de usuário de um aplicativo, encapsulando os elementos da página (como botões, campos de texto, links etc.) e as operações que podem ser realizadas nesses elementos.

A ideia principal por trás do Page Object é separar a lógica de automação dos detalhes da implementação da interface do usuário. Isso torna o código de automação mais limpo, modular e fácil de manter. Além disso, quando há alterações na interface do usuário, apenas os Page Objects afetados precisam ser atualizados, em vez de modificar o código de automação em vários lugares.

Para acessar a pagina de docs click no [link](https://codecept.io/pageobjects/)

## Pré requisitos

* Ter configurado a etapa da tag `configurando-codeceptJS` [link](./codeceptJS.md)

## Passos da configuração
- [X] Primeiro passo montar a estrutura que vou utilizar e explicar
- [X] Segundo passo configurar o arquivo `codecept.conf.js`
- [X] Terceiro passo configurar todos os arquivos `features`, `steps` e `pages`

Logo abaixo mais detalhes sobre a execução de cada passo.

### Primeiro passo: montar a estrutura que vou utilizar e explicar

Segue um modelo da estrutura que irei utilizar:
```
├─PROJETO-CV
│   ├──features
│   └──pages
│       └──login.page.js   
│   ├──Readme
│   │   ├──codeceptJS.md
│   │   ├──comandosGit.md
│   │   ├──gherkin.md      
│   │   └──pageObject.md   
│   ├──steps
│   │   └──login.step.js         
├─.gitignore
├─codecept.conf.js
├─jsconfig.json
├─package-lock.json
├─package.json
├─README.md   
├─steps_file.js
└─steps.d.ts
```
* Uma breve descrição sobre a estrutura
  * `PROJETO-CV`: Raiz do projeto
  * `features`: Diretório onde será criado todos os arquivos `.feature` do projeto
  * `Readme`: Diretório onde armazeno todos os readme que estou fazendo do projeto
  * `steps`: Diretório onde será criado todos os arquivos `.step.js` do projeto
  * `pages`: Diretório onde será criado todos os arquivos `.page.js` do projeto

### Segundo passo: configurar o arquivo ***codecept.conf.js***

 Dentro do arquivo `codecept.conf.js` na etapa onde possui informações do gherkin alterar o caminho do steps para ficar de acordo com a estrutura proposta no projeto.
  ```
  
  hooks: [],
  gherkin: {
    features: './features/*.feature',
    steps: './steps/*'
  },
  ```

### Terceiro passo: configurar todos os arquivos ***features***, ***steps*** e ***pages***

Dentro da pasta `features`, alterei o nome do arquivo `basic.feature` para `login.feature`, para ficar mais legível que dentro desse arquivo vai conter todos os cenários referente ao login.

A pasta `step_definitions` alterei seu nome para `steps`, e alterei o arquivo que estava dentro da pasta de `steps.js` para `login.step.js`, com o mesmo intuito de ficar mais legível e dentro deste arquivo vai conter todos os steps referente ao login.

Criada a pasta nova `pages`, adicionado dentro dessa pasta o arquivo `login.page.js`, com o mesmo intuito de ficar mais legível e dentro deste arquivo vai conter todos o mapeamento da página referente ao login.

Segue um exemplo de como fica a estrutura dos arquivos correspondente a cada pasta:
* `feature`, contém a estrutura do gherkin, conforme exemplo:
  ```
  # language:pt
  Funcionalidade: Login
  Como usuário do sistema Swag Labs
  Desejo realizar o login no sistema
  Para realizar minhas tarefas

  Cenário: Login com sucesso
    Dado acesse a pagina "Swag Labs"
    E informe o usuário "standard_user"
    E informe a senha "secret_sauce"
    Quando clico no botão login
    Então o sistema apresenta a tela de "Products"
  ```
* `step`, contém a estrutura que faz a ligação entre os nomes das steps do gherkin com os métodos criado na page e alguma lógica caso necessário, conforme exemplo:
  ```
  const loginPage = require('../pages/login.page');

  Given ('acesse a pagina {string}', async(page)=>{
    await loginPage.accessPage(page);
  });

  Given ('informe o usuário {string}', async(user)=>{
    await loginPage.setUser(user);
  });

  Given ('informe a senha {string}', async(password)=>{
    await loginPage.setPassword(password);
  });

  When ('clico no botão login', async()=>{
    await loginPage.clickLogin();
  });

  Then ('o sistema apresenta a tela de {string}', async(page)=>{
    await loginPage.assertPageTitle(page);
  });
  ```
* `page`, contém exclusivamente o mapeamento da página, as logica fica nos steps, na page apenas a comunicação da pagina e seu retorno, conforme exemplo:
    ```
    const I = actor();

    module.exports = {

      div:{
        logo:'//div[@class="login_logo"]',
      }, 
      input:{
        userName: '//input[@id="user-name"]',
        password: '//input[@id="password"]',
        login:'//input[@id="login-button"]'
      },
      span:{
        title:'//span[@class="title"]'
      },
  
      accessPage(pageLogo) {
        I.amOnPage('/');
        I.waitForElement(this.div.logo);
        I.seeTextEquals(pageLogo, this.div.logo);
      },
      setUser(user){
        I.waitForElement(this.input.userName);
        I.fillField(this.input.userName,user);
      },
      setPassword(password){
        I.waitForElement(this.input.password);
        I.fillField(this.input.password,password);
      },
      clickLogin(){
        I.waitForElement(this.input.login);
        I.click(this.input.login);
      },
      assertPageTitle(pageTitle){
        I.waitForElement(this.span.title);
        I.seeTextEquals(pageTitle,this.span.title);
      }
    }
    ```
