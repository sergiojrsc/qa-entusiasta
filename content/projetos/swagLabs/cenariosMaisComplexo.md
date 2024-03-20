+++
title = " "
linktitle = "Cenário mais complexo"
weight = 50
+++
# Criando um cenário mais complexo utilizando algumas funcionalidades

Criar um cenário um pouco mais complexo para demonstrar o uso de algumas funcionalidades que vai auxiliar na automação.

O intuito é criar um cenário onde clique em todos os produtos para serem adicionados no carrinho. Ao fazer este teste na página Swag Labs, podemos verificar o cenário funcionando e simular o mesmo cenário com problema, alterando apenas o usuário.

Segue os usuários que vão ser utilizados:
* `standard_user` este usuário não possui erro.
* `problem_user` este usuário possui erro.

## Pré requisitos
* Ter configurado a etapa da tag `configurando-codeceptJS` [link](./codeceptJS.md)
* Ter configurado a eta da tag `configurando-gherkin` [link](./gherkin.md)
 
## Passos da configuração
- [X] Primeiro passo configurar o `expect`
- [X] Segundo passo configurar o `loadsh`
- [X] Terceiro passo lógica no step
- [X] Quarto passo esquema do cenário


Logo abaixo mais detalhes sobre a execução de cada passo.

### Primeiro passo configurar o expect

O "Expect.js" é uma biblioteca de código aberto escrita em JavaScript para testes de unidade e TDD (Desenvolvimento Orientado a Testes) em aplicativos JavaScript. Ele é usado principalmente no desenvolvimento de software para automatizar e simplificar o processo de teste.

O Expect.js fornece uma sintaxe de asserção que é fácil de ler e escrever, permitindo que os desenvolvedores definam comportamentos esperados em seus testes de forma clara e concisa. Ele oferece uma variedade de métodos para testar valores, incluindo igualdade estrita, igualdade profunda, presença de propriedades, entre outros.

Para fazer a instalação dessa biblioteca, executar o seguinte comando conforme orientação da página do npm no [link](https://www.npmjs.com/package/expect.js):
```
npm i expect.js@0.3.1
```
Para saber mais informações de quais métodos utilizar, eu sempre consulto esse [link](https://www.chaijs.com/api/bdd/)

Segue um exemplo de como utilizei no projeto:
```
const expect = require('expect.js');
const _ =require('lodash');

const productsPage = require('../pages/produtcs.page');

Given ('adicionar todos os produtos no carrinho', async()=>{
    let listNameProducts = []
    listNameProducts = await productsPage.getListNameAllProducts();
    for (const key in listNameProducts) {
        await productsPage.clickAddToCartProduct(listNameProducts[key])
    }
});

Then ('a quantidade de produtos adicionado no carrinho deve ser a mesma quantidade de produtos exibido', async()=>{
    const quantityProduct = await productsPage.getQuantityProducts();
    const quantityAddToCart = _.toNumber(await productsPage.getNumberProductAddToCart());
    expect(quantityAddToCart).to.equal(quantityProduct.length);
});

```

* Para fazer a importação da biblioteca utilizei a seguinte linha de código:
    ```
    const expect = require('expect.js');
    ```
* Para fazer a validação da quantidade de produtos que está sendo exibido no carrinho é igual a quantidade de produtos que foram clicados para serem adicionados:
  ```
  expect(quantityAddToCart).to.equal(quantityProduct.length);
  ```
  * `expect`: Esta é a função de asserção, usada para definir uma asserção nos testes.
  * `quantityAddToCart`: Variável onde foi armazenada a quantidade que foi adicionada ao carrinho.
  * `.to.equal(quantityProduct.length)`: Este é o método de asserção **.to.equal(...)**, que verifica se o valor **quantityAddToCart** é igual ao comprimento (length) de **quantityProduct**. Se forem iguais, o teste passa, caso contrário, o teste falha.

### Segundo passo configurar o loadsh

Lodash é uma biblioteca JavaScript de utilitários que simplifica a manipulação de dados em JavaScript. Ela fornece funções de utilitário para trabalhar com arrays, objetos, strings, funções, e mais, de forma consistente e eficiente em termos de desempenho.

Para fazer a instalação dessa biblioteca executar o seguinte comando conforme orientação da página do npm no [link](https://www.npmjs.com/package/lodash):
```
npm i lodash
```
Para saber mais informações de quais métodos utilizar, eu sempre consulto esse [link](https://lodash.com/docs/4.17.15)

Segue um exemplo de como utilizei no projeto:
Segue um exemplo de como utilizei no projeto:
```
const expect = require('expect.js');
const _ =require('lodash');

const productsPage = require('../pages/produtcs.page');

Given ('adicionar todos os produtos no carrinho', async()=>{
    let listNameProducts = []
    listNameProducts = await productsPage.getListNameAllProducts();
    for (const key in listNameProducts) {
        await productsPage.clickAddToCartProduct(listNameProducts[key])
    }
});

Then ('a quantidade de produtos adicionado no carrinho deve ser a mesma quantidade de produtos exibido', async()=>{
    const quantityProduct = await productsPage.getQuantityProducts();
    const quantityAddToCart = _.toNumber(await productsPage.getNumberProductAddToCart());
    expect(quantityAddToCart).to.equal(quantityProduct.length);
});

```
* Para fazer a importação da biblioteca utilizei o seguinte linha de código:
    ```
    const _ =require('lodash');
    ```
* Utilizei a função **toNumber** do loadsh para converter uma variável que veio em string para número.
  * `const quantityAddToCart`: criação da variável que vai receber a quantidade de produtos que foi adicionado no carrinho.
  * `_.toNumber`: Esta é uma função do Lodash que converte o valor passado para um número. O _ é uma convenção comum usada para importar o Lodash.
  * `await productsPage.getNumberProductAddToCart()`: Função onde vai pegar o valor que mostra quantos produtos foram adicionados no carrinho

### Terceiro passo lógica no step
Dentro do steps podemos utilizar algumas lógicas do tipo for, if, entre outras para fazer as validações necessárias que precisamos.

Segue um exemplo de como foi utilizado:
```
Given ('adicionar todos os produtos no carrinho', async()=>{
    let listNameProducts = []
    listNameProducts = await productsPage.getListNameAllProducts();
    for (const key in listNameProducts) {
        await productsPage.clickAddToCartProduct(listNameProducts[key])
    }
});
```
* Para criar o step eu precisei clicar no botão de adicionar de todos os produtos que está sendo mostrado na tela:
  * `let listNameProducts = []`: Criei uma variável do tipo let para receber um objeto, que é a lista de produtos.
  * `await productsPage.getListNameAllProducts();`: Método que retorna a lista de todos os nomes dos produtos que existem na página.
  * `listNameProducts = await productsPage.getListNameAllProducts();`: Estou adicionando a lista de produtos dentro da variável.
  * Foi criado um for para fazer a interação com todos os produtos:
    * `for (const key in listNameProducts)`: Este é um loop for-in que itera sobre todas as chaves do objeto listNameProducts. Para cada iteração, a variável key contém a posição da chave onde será pego o nome do produto.
    * `await productsPage.clickAddToCartProduct(listNameProducts[key])`: Método criado para clicar no botão de adicionar no carrinho, quando informado o nome de um produto
  

## Quarto passo esquema do cenário
Adicionado o esquema de cenário para fazer a repetição do mesmo cenário com dois usuários diferentes, como a aplicação disponibiliza um usuário com problema e um que funciona, vou utilizar o esquema do cenário para passar o usuário com problema no mesmo cenário para demonstrar como seria exibido o erro caso tenha erro.

Segue um exemplo de como foi utilizado:
```
# language:pt
Funcionalidade: Products
  Como usuário do sistema Swag Labs
  Desejo acessar a pagina de produtos
  Para adicionar os produtos no carrinho

  Esquema do Cenário: Adicionar todos os produtos no carrinho
    Dado acessar a pagina "Swag Labs" com o usuário <user>
    Quando adicionar todos os produtos no carrinho
    Então a quantidade de produtos adicionado no carrinho deve ser a mesma quantidade de produtos exibido
    Exemplos:
    | user            | 
    | 'standard_user' |
    | 'problem_user'  |
```
* Em vez de só adicionar o `Cenário` é adicionado `Esquema do Cenário`
* Na variável onde recebe os valores deve ser alterado, colocando o nome dela no meio dos sinais de menor e maior `<user>`
* No final do cenário é adicionado o step de `Exemplos` e abaixo dele uma tabela, onde a primeira linha é a variável e as linhas abaixo o valor que será utilizado:
  ```
    | user            | 
    | 'standard_user' |
    | 'problem_user'  |
  ```
