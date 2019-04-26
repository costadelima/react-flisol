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

Na próxima parte do workshop iremos construir uma aplicação mais interessante: Uma cópia do Instagram.

[Prosseguir para a próxima parte](../../instagram)