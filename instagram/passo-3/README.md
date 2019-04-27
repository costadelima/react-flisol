## Chegamos ao fim

Uma possível implementação para os componentes é a seguinte:

`Post.js`:

```jsx
import React from 'react';
import CabecalhoPost from './CabecalhoPost';
import ImagemPost from './ImagemPost';
import AcoesPost from './AcoesPost';
import ContagemCurtidas from './ContagemCurtidas';
import Comentarios from './Comentarios';

const styles = {
  post: {
    marginTop: 16
  }
};

class Post extends React.Component {
  state = {
    contagemLikes: this.props.post.contagemLikes,
    curtido: false
  };

  get possuiComentarios () {
    const { post } = this.props;
    return Boolean(post.comentarios && post.comentarios.length > 0);
  }

  curtirPostagem = (curtir) => {
    const { contagemLikes } = this.state;
    this.setState({
      contagemLikes: contagemLikes + (curtir ? 1 : -1),
      curtido: curtir
    });
  };

  render () {
    const { post } = this.props;
    const { contagemLikes, curtido } = this.state;

    return (
      <div style={styles.post}>
        <CabecalhoPost
          thumbUrl={post.thumbUrl}
          nomeUsuario={post.nomeUsuario}
          localizacao={post.localizacao}
        />
        <ImagemPost postUrl={post.postUrl} />
        <AcoesPost
          curtirPostagem={this.curtirPostagem}
          curtido={curtido}
        />
        <ContagemCurtidas contagemLikes={contagemLikes} />
        {this.possuiComentarios &&
          <Comentarios comentarios={post.comentarios} />}
      </div>
    );
  }
};

export default Post;
```

`CabecalhoPost.js`:

```jsx
import React from 'react';

const styles = {
  avatar: {
    borderRadius: '50%',
    display: 'block'
  },
  cabecalho: {
    display: 'flex',
    flexDirection: 'row',
    padding: '12px 16px'
  },
  titulo: {
    display: 'flex',
    flexDirection: 'column',
    justifyContent: 'center',
    paddingLeft: 8
  },
  nomeUsuario: {
    fontSize: 14,
    fontWeight: 'bold'
  },
  localizacao: {
    fontSize: 12
  }
};

const CabecalhoPost = ({ thumbUrl, nomeUsuario, localizacao }) => {
  return (
    <div style={styles.cabecalho}>
        <div>
          <img
            style={styles.avatar}
            src={thumbUrl}
            alt={`Avatar do usuário ${nomeUsuario}`}
          />
        </div>
        <div style={styles.titulo} >
          <div style={styles.nomeUsuario}>{nomeUsuario}</div>
          <div style={styles.localizacao}>{localizacao}</div>
        </div>
      </div>
  );
};

export default CabecalhoPost;
```

`ImagemPost.js`:

```jsx
import React from 'react';

const ImagemPost = ({ postUrl }) => {
  return (
    <div>
      <img
        src={postUrl}
        alt="Imagem do post"
      />
    </div>
  );
};

export default ImagemPost;
```

`AcoesPost.js`:

```jsx
import React from 'react';
import { FontAwesomeIcon } from '@fortawesome/react-fontawesome';
import { faHeart, faComment } from '@fortawesome/free-regular-svg-icons';
import { faHeart as faHeartFull }  from '@fortawesome/free-solid-svg-icons';

const styles = {
  acoes: {
    fontSize: 24,
    padding: '8px 16px'
  }
};

const AcoesPost = ({ curtirPostagem, curtido }) => {
  return (
    <div style={styles.acoes}>
      {curtido
        ? <FontAwesomeIcon
            style={{ marginRight: 16, color: 'red' }}
            icon={faHeartFull}
            onClick={() => curtirPostagem(false)}
          />
        : <FontAwesomeIcon
            style={{ marginRight: 16 }}
            icon={faHeart}
            onClick={() => curtirPostagem(true)}
          />
      }
      <FontAwesomeIcon icon={faComment} />
    </div>
  );
};

export default AcoesPost;
```

`ContagemCurtidas.js`:

```jsx
import React from 'react';

const styles = {
  curtidas: {
    padding: '4px 16px',
    fontSize: 14,
    fontWeight: 'bold'
  }
};

const ContagemCurtidas = ({ contagemLikes }) => {
  return (
    <div style={styles.curtidas}>{contagemLikes} curtidas</div>
  );
};

export default ContagemCurtidas;
```

`Comentarios.js`:

```jsx
import React from 'react';

const styles = {
  containerComentario: {
    display: 'flex',
    padding: '4px 16px'
  },
  comentario: {
    fontSize: 14,
    marginLeft: 4,
    textOverflow: 'ellipsis',
    overflow: 'hidden',
    whiteSpace: 'nowrap'
  },
  nomeUsuario: {
    fontSize: 14,
    fontWeight: 'bold'
  },
};

const Comentarios = ({ comentarios }) => {
  return (
    <div>
      {comentarios.map((comentario, index) => 
        <div key={index} style={styles.containerComentario}>
          <div style={styles.nomeUsuario}>{comentario.nomeUsuario}</div>
          <div style={styles.comentario}>{comentario.textoComentario}</div>
        </div>
      )}
    </div>
  );
};

export default Comentarios;
```