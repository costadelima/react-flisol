## A primeira aplicação

Uma simples aplicação com uma lista de tarefas com o intuito de conhecer os conceitos básicos do desenvolvimento web com React. A aplicação terá os seguintes elementos:

* Uma lista de tarefas
* Um campo de texto para uma nova tarefa
* Um botão para inserir

Use o React Creat App para gerar uma aplicação funcional em React:

```bash
$ create-react-app lista-tarefas
$ cd lista-tarefas
```

Para iniciar a aplicação basta usar:

```bash
$ npm start
```

No arquivo `App.js`, subsitua todo o conteúdo por:

```jsx
import React from 'react';

function App() {
  return (
    <div>Minha primeira aplicação</div>
  );
}

export default App;
```

Substitua a `div` uma lista de tarefas com os seguintes elementos:

* Me inscrever no FLISoL
* Aprender React
* Fazer minha primeira aplicação

> Para criar uma lista com HTML use elementos `li` aninhados dentro de uma `ul`.