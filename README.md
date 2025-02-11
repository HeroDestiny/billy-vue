## Vue.js Componentes

Os componentes são blocos de construção essenciais do Vue.js. Eles desempenham um papel central na arquitetura do framework, permitindo que você crie partes reutilizáveis e independentes da interface do usuário, cada uma com sua própria lógica, template e estilo.

### Criando um Componente

Para criar um novo componente, basta criar um arquivo `.vue` dentro da pasta `components` do seu projeto Vue.

**Estrutura de um Componente:**

O código de um componente em Vue.js consiste em três partes principais:

- A seção `<template>` (HTML do componente)
- A seção `<script>` (lógica do componente)
- A seção `<style>` (estilos do componente)

Exemplo:

```vue
<template>
  <div>
    <h1>{{ titulo }}</h1>
  </div>
</template>

<script>
export default {
  data() {
    return {
      titulo: "Olá, Vue!"
    };
  }
};
</script>

<style scoped>
h1 {
  color: blue;
}
</style>
```

### Usando um Componente

Para usar um componente dentro de outro, basta importá-lo e registrá-lo no objeto `components`.

Exemplo:

```vue
<template>
  <div>
    <MeuComponente />
  </div>
</template>

<script>
import MeuComponente from "@/components/MeuComponente.vue";

export default {
  components: {
    MeuComponente
  }
};
</script>
```

### Comunicação entre Componentes

Os componentes podem se comunicar entre si através de `props` e `events`.

#### Props (Entrada de Dados)

Permitem que um componente pai passe dados para um componente filho.

_Componente Filho:_

```vue
<template>
  <p>{{ mensagem }}</p>
</template>

<script>
export default {
  props: ["mensagem"]
};
</script>
```

_Componente Pai:_

```vue
<template>
  <MeuFilho :mensagem="mensagemDoPai" />
</template>

<script>
import MeuFilho from "@/components/MeuFilho.vue";

export default {
  components: { MeuFilho },
  data() {
    return {
      mensagemDoPai: "Olá do Pai!"
    };
  }
};
</script>
```

#### Emitindo Eventos (Saída de Dados)

Permitem que um componente filho envie eventos para um componente pai.

_Componente Filho:_

```vue
<template>
  <button @click="enviarMensagem">Enviar Mensagem</button>
</template>

<script>
export default {
  emits: ["mensagemEnviada"],
  methods: {
    enviarMensagem() {
      this.$emit("mensagemEnviada", "Mensagem do Filho");
    }
  }
};
</script>
```

_Componente Pai:_

```vue
<template>
  <MeuFilho @mensagemEnviada="acaoNoPai" />
</template>

<script>
import MeuFilho from "@/components/MeuFilho.vue";

export default {
  components: { MeuFilho },
  methods: {
    acaoNoPai(evento) {
      alert(evento);
    }
  }
};
</script>
```

[Documentação Oficial Vue - Props & Events](https://vuejs.org/guide/components/props.html)

### Ciclo de Vida de um Componente Vue.js

O Vue fornece uma série de eventos de ciclo de vida que ocorrem desde a criação até a destruição de um componente.

#### `mounted`

Chamado após a montagem do componente.

```vue
<script>
export default {
  mounted() {
    console.log("Componente montado!");
  }
};
</script>
```

#### `watch`

O watch permite monitorar mudanças em propriedades específicas do componente.

```vue
<script>
export default {
  data() {
    return {
      contador: 0
    };
  },
  watch: {
    contador(novoValor) {
      console.log("Contador atualizado para: ", novoValor);
    }
  }
};
</script>
```

#### `beforeUnmount`

Chamado antes de um componente ser destruído.

```vue
<script>
export default {
  beforeUnmount() {
    console.log("Componente será destruído!");
  }
};
</script>
```

[Documentação Oficial Vue - Lifecycle](https://vuejs.org/guide/essentials/lifecycle.html)

## Prática

Aqui está a sugestão para a prática:

**Tema do Projeto:** Lista de Tarefas

**Descrição:** Criar uma aplicação de Lista de Tarefas (*To-Do List*), onde os usuários podem adicionar, marcar como concluídas e remover tarefas. A aplicação deve ser desenvolvida usando Vue.js, aplicando os conceitos aprendidos na aula.

**Requisitos:**

- Criar um componente para o cabeçalho do sistema;
- Criar um componente para o input de inclusão de tarefas;
- Criar um componente de apresentação das tarefas em uma lista.

