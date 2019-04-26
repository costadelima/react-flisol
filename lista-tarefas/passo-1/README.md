## Passo 1

O código do passo anterior será algo parecido com:

```jsx
return (
  <div>
    <h1>Minhas tarefas:</h1>
    <ul>
      <li>Me inscrever no FLISoL</li>
      <li>Aprender React</li>
      <li>Fazer minha primeira aplicação</li>
    </ul>
  </div>
);
```

### Criando o Primeiro Componente

Crie uma nova pasta chamada `componentes` dentro de `src`. Dentro da pasta crie o arquivo `TelaPrincipal.js` com o mesmo código `html` do `App.js`.

O conteúdo do arquivo será algo parecido com:

```jsx
import React from 'react';

class TelaInicial extends React.Component {
  render() {
    return (
      <!-- Código HTML com a lista de tarefas -->
    );
  }
}

export default TelaInicial;
```

> Todo arquivo com um componente React deve ter a declaração de `import` do React.

Importe o novo componente em `App.js` e o declare como uma tag `html`:

```jsx
import React from 'react';
import TelaInicial from './componentes/TelaInicial';

function App() {
  return (
    <TelaInicial />
  );
}

export default App;
```

### Adicionando Código dentro do HTML

O `jsx` permite que o `html` se torne dinâmico por meio de instruções em ECMAScritpt. Como por exemplo:

```jsx
render() {
  const textoDinamico = 'Um texto qualquer';
  const arranjoTextos = ['Texto 1', 'Texto 2', 'Texto 3'];
  const condicao = true;

  return (
    <div>
      <!-- Insere o valor de textoDinamico dentro da div -->
      <div>{textoDinamico}</div>

      <!-- Gera 3 elementos de div com o valor de texto -->
      {arranjoTextos.map(texto => <div>{texto}</div>)}

      <!-- Condicional de render -->
      {condicao &&
        <span>Só é exibido se condição = true</span>}
    </div>
  );
}
```

Agora vamos colocar em prática. Altere o componente `TelaInicial.js` para gerar a lista de tarefas dinâmicamente.

[Prosseguir para a próxima parte](./passo-2)