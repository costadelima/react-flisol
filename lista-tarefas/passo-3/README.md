## Criando uma Lista de Tarefas

Agora sabemos alguns dos conceitos mais importantes do React: usar o `state`. O código de toda a aplicação será parecido com:

```jsx
import React from 'react';

class TelaInicial extends React.Component {
  state = { 
    listaTarefas: [
      'Me inscrever no FLISoL',
      'Aprender React',
      'Fazer minha primeira aplicação'
    ],
    novaTarefa: ''
  };

  alterarTextoTarefa = ({ target: { value } }) => {
    this.setState({ novaTarefa: value });
  };

  inserirTarefa = () => {
    const novaLista = this.state.listaTarefas
      .concat(this.state.novaTarefa);

    this.setState({
      listaTarefas: novaLista
    });
  };

  render() {
    const { listaTarefas } = this.state;
    return (
      <div>
        <h1>Minhas tarefas:</h1>
        <ul>
          {listaTarefas.map(tarefa => <li>{tarefa}</li>)}
        </ul>

        <h2>Inserir nova tarefa:</h2>
        <input type="text" onChange={this.alterarTextoTarefa} />
        <button onClick={this.inserirTarefa}>Inserir</button>
      </div>
    );
  }
}

export default TelaInicial;
```

# Refatorando em Componentes

Um dos aspectos mais importantes do React é permitir a modularidade do código por meio de componentes. Poderiamos extrair a lista de tarefas para um novo componente:

`ListaTarefas.js`
```jsx
class ListaTarefas extends React.Component {
  render() {
    const { listaTarefas } = this.props;
    return (
      <div>
        <h1>Minhas tarefas:</h1>
        <ul>
          {listaTarefas.map(tarefa => <li>{tarefa}</li>)}
        </ul>
      </div>
    );
  }
}
```

E declararmos uma `<ListaTarefas>` no componente `TelaInicial`:

```jsx
<ListaTarefas listaTarefas={listaTarefas} />
```

> No React, parâmetros de um componente são passados como fossem atributos HTML. Dentro do código ECMAScript podemos acessar esses parâmetros via a propriedade `this.props`;

Na próxima parte do workshop iremos construir uma aplicação mais interessante: Uma cópia do Instagram.

[Prosseguir para a próxima parte](../../instagram)