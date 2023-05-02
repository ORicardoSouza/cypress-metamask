# Como conectar o Metamask com o Cypress

Este guia irá ajudá-lo a conectar o Metamask com o Cypress para que você possa testar sua aplicação web baseada em blockchain.

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte instalado em seu sistema:

- Node.js
- npm
- Metamask
- Cypress

## Passo 1: Instalar o pacote `cypress-metamask`

Abra o terminal e navegue até o diretório raiz do seu projeto. Em seguida, execute o seguinte comando para instalar o pacote `cypress-metamask`:

```jS
npm install cypress-metamask
```

## Passo 2: Configurar o Metamask

Para conectar o Metamask com o Cypress, você precisará fornecer algumas informações de configuração. Para fazer isso, siga as etapas abaixo:

1. Abra o Metamask e crie uma nova conta ou use uma existente.

2. Copie a frase-semente da sua conta Metamask.

3. No arquivo `cypress.json`, adicione a seguinte configuração:

```json
{
  "env": {
    "METAMASK_SEED_PHRASE": "<sua frase-semente do metamask>",
    "METAMASK_PASSWORD": "<sua senha do metamask>",
    "METAMASK_ACCOUNT_INDEX": "<o índice da sua conta metamask>"
  }
}
```

Certifique-se de substituir `<sua frase-semente do metamask>`, `<sua senha do metamask>` e `<o índice da sua conta metamask>` pelas informações corretas.

## Passo 3: Adicionar o plugin `cypress-metamask` no arquivo de suporte do Cypress

No arquivo `cypress/support/index.js`, adicione o seguinte código:

```js
import 'cypress-metamask'
```

## Passo 4: Escrever seus testes Cypress

No arquivo de teste Cypress que você deseja usar o Metamask, adicione o seguinte código:

```js
describe('Minha descrição de teste', () => {
  beforeEach(() => {
    cy.task('metamaskSetup')
  })

  it('Meu primeiro teste', () => {
    cy.metamaskLogin()
    cy.visit('<seu URL de teste>')
    // Faça o que você precisa fazer para testar a sua aplicação
  })
})
```

Certifique-se de substituir `<seu URL de teste>` pelo URL correto da sua aplicação.

## Passo 5: Executar seus testes Cypress

Finalmente, execute seus testes Cypress usando o seguinte comando:

```js
npx cypress run
```

Isso deve permitir que você conecte o Metamask ao Cypress e execute seus testes automatizados.

## Conclusão

Espero que este guia tenha sido útil para você conectar o Metamask com o Cypress. Se você tiver alguma dúvida ou problema, não hesite em entrar em contato com a comunidade Cypress ou Metamask para obter ajuda adicional.
