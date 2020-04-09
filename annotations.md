emotions como uma alternativa a styled components. Os dois são igualmente populares.

Nesse projeto, ele irá utilizar css modules (css-loader e style-loader) e css-in-js, para mostrar como configurar os testes com jest nesses casos.

adicionar testes num projeto que já existe:

`npm i jest`

test script:
`npm t`

spec ou test ou \_\_tests__
contanto que tenha um it/ ou test(), funciona.

o validate da typagem agora acrescenta o teste. lint, test, build. o travis (CI) roda isso.

Várias pastas \_\_tests__?

## problema 1: usar um arquivo de teste com import statement E webpack com tree-shaking
- nos meus projetos, tendo um babelrc c/ preset-env basta para compilar os ESImports.
Nesse projeto do Kent com webpack, a compilação de modules está sendo feita pelo webpack.
Kent quer que o webpack cuide disso, porque ele não compila código desnecessário, acho (tree-shaking)

entendi que quando o jest roda, ele coloca ```javascript process.env.NODE_ENV === 'test'```, e ele usa isso no babelrc.js para compilar como common.js modules quando é test.

## fazer o jest funcionar no ambiente node e no ambiente de browser (jsdom), ou ambos.
não usar jsdom se não for necessário:
``` $ npm test -- --env=node ```
roda os testes no ambiente node.

para configurar isso para não precisar passar a flag o tempo inteiro, cria-se o jest.config.js

```javascript
module.exports = {
  testEnviroment: 'jest-enviroment-node'
}
```

## testando auto-scaling-text.js
Jest dá um erro de compilação. Jest não consegue importar um css module auto-scaling-text.module.css como se fosse um módulo de common.js, ao invés de uma rquivo css.

Vamos fazer um mock desse arquivo.

```javascript
module.exports = {
  moduleNameMapper: {
    '\\.css$': require.resolve('./test/style-mock.js')
  }
}
// style-mock.js:
module.exports = {}
```

## outras formas de lidar com css modules e webpack..
package identity-obj-proxy

i don't care for now.

## 