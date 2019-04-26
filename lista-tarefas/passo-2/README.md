## Passo 2

O código do passo anterior será algo parecido com:

```jsx
render() {
  const listaTarefas = [
    'Me inscrever no FLISoL',
    'Aprender React',
    'Fazer minha primeira aplicação'
  ];

  return (
    <div>
      <h1>Minhas tarefas:</h1>
      <ul>
        {listaTarefas.map(tarefa => <li>{tarefa}</li>)}
      </ul>
    </div>
  );
}
```

### Inserindo novas tarefas

Agora crie um campo de texto para o usuário entrar com uma nova tarefa. Crie também um botão para submeter o texto inserido.

O código será parecido com o seguinte:

```html
  <h2>Inserir nova tarefa:</h2>
  <input type="text" />
  <button>Inserir</button>
```

Como receber a entrada de texto e gravar em uma variável? Como alterar a lista de tarefas para inserir uma nova entrada? A resposta para essas perguntas é usar o `state` do componente.

### O State

O estado do componente permite que a aplicação armazene dados e os altere em tempo de execução sem precisar regarregar a página. Veja o exemplo a seguir, onde um contador é incrementado a cada *click* do usuário.

```jsx
class MeuComponente extends React.Component {
  state = {
    contador: 0 // estado inicial
  };

  incrementar = () => {
    // a função setState permite alterar o estado do componente
    this.setState({
      contador: this.state.contador + 1
    });
  }

  render() {
    return (
      <div>
        <span>Contador: {this.state.contador}</span>
        <button onClick={this.incrementar}>Incrementar</button>
      </div>
    );
  }
}
```

Agora faça o mesmo para a nossa aplicação. Teremos um estado inicial com: 

```js
state = {
  listaTarefas: [...],
  novaTarefa: ''
};
```

Implemente duas funções, uma para receber o input do usuário no campo de texto e outra para inserir a nova tarefa.

> O elemento `input` possui o listener `onChange`, que recebe como parâmetro o evento `e`. Para acessar o conteúdo digitado use `e.target.value`.

> De forma similar, o elemento `button` possui o listener `onClick`.

[Prosseguir para a próxima parte](../passo-3)