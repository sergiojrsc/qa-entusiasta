+++
title = " "
linktitle = "Gherkin"
weight = 30
+++
# Gherkin

Gherkin é uma linguagem de especificação utilizada para descrever o comportamento esperado de um software, principalmente em testes de aceitação e desenvolvimento orientado a comportamento (BDD - Behavior Driven Development). É uma linguagem simples e legível que permite aos desenvolvedores, testadores e stakeholders expressarem os requisitos do software de uma forma estruturada e compreensível por todos os envolvidos no projeto.

As especificações escritas em Gherkin seguem uma sintaxe padronizada, utilizando palavras-chave como "Dado" (Given), "Quando" (When), "Então" (Then) e outras para descrever o comportamento do sistema em diferentes cenários. Essas especificações podem então ser executadas por ferramentas de automação de testes que interpretam a linguagem Gherkin e executam os testes correspondentes no software.

A vantagem do Gherkin é que ele facilita a comunicação entre diferentes partes interessadas no projeto, ajuda a garantir que todos tenham uma compreensão clara dos requisitos do software e permite a automação eficiente dos testes de aceitação.

Para acessar a pagina de docs click no [link](https://cucumber.io/docs/gherkin/reference/)

## Pré requisitos

* Ter configurado a etapa da tag `configurando-codeceptJS` [link](./codeceptJS.md)
 
 
## Passos da configuração
- [X] Primeiro passo executar o comando `npm init -y` para criar o arquivo package.json
- [X] Segundo passo adicionar as informações nos arquivos `basic.feature` e `steps.js`
- [X] Terceiro passo excluir um arquivo que não está mais sendo utilizado
- [X] Quarto passo configurar para entender os comandos do gherkin em português
- [X] Quinto passo executar o teste

Logo abaixo mais detalhes sobre a execução de cada passo.

### Primeiro passo executar o comando `npx codeceptjs gherkin:init` para criar o arquivo package.json
* O comando npx codeceptjs gherkin:init é usado para inicializar um projeto CodeceptJS com suporte a Gherkin. Aqui está o que esse comando faz:

  * npx: é um utilitário do Node.js que permite executar pacotes do npm que não estão instalados globalmente. Ele baixa temporariamente o pacote necessário, executa o comando e, em seguida, o remove.

  * codeceptjs: é uma estrutura de teste de interface do usuário (UI) para JavaScript. Permite escrever testes de aceitação automatizados de forma simples e eficaz.

  * gherkin:init: é um comando específico do CodeceptJS para inicializar um projeto com suporte a Gherkin. Gherkin é uma linguagem de especificação que permite descrever o comportamento do software de uma forma estruturada e legível.

  Portanto, ao executar `npx codeceptjs gherkin:init`, você está inicializando um projeto CodeceptJS com suporte a Gherkin, o que significa que poderá escrever seus testes de aceitação usando a sintaxe Gherkin e executá-los usando o CodeceptJS. Isso é útil para criar testes automatizados que são fáceis de entender e manter, especialmente em projetos orientados a comportamento (BDD).

Ao executar esse comando o projeto irá sofrer as seguintes alterações:
 
* Será criado as seguintes pastas:
   *  `feateures`
   *  `step_def`
* Dentro das pastas foram criados dois arquivos de exemplos de como funciona a estrutura:
  * `basic.feature`
  * `steps.js`
* Dentro do arquivo `codecept.conf.js` foi adicionado os seguintes comandos:
  ```
  mocha: {},
  bootstrap: null,
  timeout: null,
  teardown: null,
  hooks: [],
  gherkin: {
    features: './features/*.feature',
    steps: ['./step_definitions/steps.js']
  },
  plugins: {
    screenshotOnFail: {
      enabled: true
    },
    tryTo: {
      enabled: true
    },
    retryFailedStep: {
      enabled: true
    },
    retryTo: {
      enabled: true
    },
    eachElement: {
      enabled: true
    },
    pauseOnFail: {}
  },
  stepTimeout: 0,
  stepTimeoutOverride: [{
      pattern: 'wait.*',
      timeout: 0
    },
    {
      pattern: 'amOnPage',
      timeout: 0
    }
  ],
  tests: './*_test.js',
  ```
### Segundo passo adicionar as informações nos arquivos `basic.feature` e `steps.js`


* No arquivo `basic.feature`basic.feature vamos criar a feature de login que já está funcionando no formato do Gherkin:
  ```
  Feature: Login
  Como usuário do sistema Swag Labs
  Desejo realizar o login no sistema
  Para realizar minhas tarefas

  Scenario: Login com sucesso
    Given acessar a pagina Swag Labs
    And informar o usuário "standard_user"
    And informar a senha "secret_sauce"
    When clicar no botão login
    Then vejo a tela de "Products"
  ```
* No arquivo `steps.js` vamos vincular as etapas criado no feature, com os comandos que o codeceptjs terá que executar:
  ```
  Given ('acessar a pagina {string}', (page)=>{
    I.amOnPage('/');
    I.waitForElement('//div[@class="login_logo"]');
    I.seeTextEquals(page,'//div[@class="login_logo"]');
  });

  Given ('informar o usuário {string}', (user)=>{
    I.waitForElement('//input[@id="user-name"]');
    I.fillField('//input[@id="user-name"]', user);
  });

  Given ('informar a senha {string}', (password)=>{
    I.waitForElement('//input[@id="password"]');
    I.fillField('//input[@id="password"]',password);
  });

  When ('clicar no botão login', ()=>{
    I.waitForElement('//input[@id="login-button"]');
    I.click('//input[@id="login-button"]');
  });

  Then ('vejo a tela de {string}', (page)=>{
    I.waitForElement('//span[@class="title"]');
    I.seeTextEquals(page,'//span[@class="title"]');
  });
  ```
### Terceiro passo excluir um arquivo que não está mais sendo utilizado
* Como vou querer só executar os cenários do gherkin o arquivo `login_test.js` pode ser excluído
* Dentro do arquivo `codecept.conf.js` podemos excluir o trecho que contém o código `tests: './*_test.js',`


### Quarto passo configurar para entender os comandos do gherkin em português
* No início de cada arquivo .feature colocar o seguinte comando `# language:pt`, com isso o gherkin já irá conseguir entender normalmente
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
* Para entender como é o de/para consultar a documentação no [link](https://cucumber.io/docs/gherkin/languages/) procurando pela lingua que deseja utilizar

### Quinto passo executar o teste
* Executar os testes com o comando `npx codeceptjs run` para verificar se está passando sem nenhum problema.
