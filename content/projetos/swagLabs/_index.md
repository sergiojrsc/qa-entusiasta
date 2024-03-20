+++
title = " "
linktitle = "Automação da aplicação Swag Lab"
ordersectionsby = "title"
description = "Automação da aplicação Swag Lab: Este projeto tem como objetivo demonstrar meu conhecimento em testes automatizados e ficar como uma documentação do que estou aprendendo. Escolhi automatizar o Swag Labs, por ser um aplicação web que possui várias funcionalidades básicas e que já iria proporcionar explorar um conhecimento muito interessante."
+++

# Automação da aplicação Swag Lab
Este projeto tem como objetivo demonstrar meu conhecimento em testes automatizados e ficar como uma documentação do que estou aprendendo.

Escolhi automatizar o [Swag Labs](https://www.saucedemo.com/v1/index.html), por ser um aplicação web que possui várias funcionalidades básicas e que já iria proporcionar explorar um conhecimento muito interessante.

Porém o que mais me chamou a atenção, é conseguir fazer exemplos de cenários onde passando apenas um usuário diferente, consigo demonstrar o mesmo teste passando e quebrando, com isso já validando os cenários automatizados, sem ter que fazer manipulação no código para validar.

Escolhi o framework CodeceptJS, pois foi o último framework que trabalhei e achei muito interessante a estrutura utilizada, com isso estou aproveitando esse projeto para aprender a criar a estrutura do zero, pois lá só fazia manutenção. Acredito que depois que aprender a fazer com um framework me ajude a migrar para outros.

Conforme eu for aprendendo novos recursos, vou estar adicionando no checklist e criando versões específicas de cada situação com o seu readme, contendo os passos que aprendi.

Segue o link do repositório no [GitLab <i class='fab fa-gitlab'></i> ](https://gitlab.com/sergiojrsc/projeto-cv)


## Principais objetivos do projeto com seus respectivas tags
- [X] [Comandos do git que serão utilizados](./git.md) tag `criando-diretorio`
- [X] [Aprender a configurar o framework CodeceptJS](./codeceptjs.md) tag `configurando-codeceptJS`
- [X] [Utilizar o conceito de Gherkin](./gherkin.md) tag `configurando-gherkin`
- [x] [Utilizar o conceito de Page Object](./pageObject.md) tag `configurando-pageObject`
- [X] [Criando um cenário mais completo utilizando algumas funcionalidades a mais como:](./cenariosMaisComplexo.md) tag `loadsh-expect-esquemaDeCenario-logicaPageObject`
  - [X] Loadsh
  - [X] Expect
  - [x] Esquema de cenário do gherkin
  - [X] Demonstrando como fica uma lógica utilizando a ideia do Page Object
- [ ] Configurar o projeto para rodar em docker
- [ ] Configurar para rodar em CI/CD
- [ ] Configurar para gerar relatórios dos teste

## Comandos a serem executados para fazer o projeto funcionar

* Baixar o repositório na sua máquina
  ```
  git clone https://gitlab.com/sergiojrsc/projeto-cv.git
  ```

* Alterando para uma tag específica
  ```
  git checkout criando-diretorio
  ```
* Depois de baixado executar o projeto é preciso instalar as suas dependências e para isso execute o seguinte comando
  ```
  npm install
  ```
* Para executar os teste execute o seguinte comando
  ```
  npx codeceptjs run
  ```
