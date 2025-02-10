# Vue.js Data Binding

### O que é Data Binding?

O Data Binding é uma funcionalidade essencial do Vue.js. Ele permite que você conecte os dados do modelo (**dados do componente**) com o template (**interface do usuário**), garantindo que qualquer alteração feita nos dados seja refletida automaticamente na interface e vice-versa.

No Vue.js, existem dois tipos principais de data binding: **One-Way Data Binding** e **Two-Way Data Binding**.

### Interpolation `{{ }}`

A interpolação permite exibir valores do modelo no template dentro de elementos HTML.

Exemplo:

```html
<h1>{{ titulo }}</h1>
<p>{{ descricao }}</p>
```

### Property Binding `v-bind`

O Property Binding permite vincular valores das propriedades do modelo a atributos de elementos HTML usando a diretiva `v-bind`.

Exemplo:

```html
<button v-bind:disabled="isBotaoDesabilitado">Clique aqui</button>
```

ou de forma abreviada:

```html
<button :disabled="isBotaoDesabilitado">Clique aqui</button>
```

### Event Binding `v-on`

O Event Binding permite capturar eventos do usuário e vinculá-los a métodos do componente usando `v-on` ou seu atalho `@`.

Exemplo:

```html
<button v-on:click="botaoClicado">Clique aqui</button>
```

Ou de forma abreviada:

```html
<button @click="botaoClicado">Clique aqui</button>
```

### Two-Way Binding `v-model`

O Two-Way Binding mantém a sincronização bidirecional entre o modelo e o template. Qualquer alteração no modelo ou no template refletirá automaticamente no outro.

Exemplo:

```html
<input v-model="nome">
<p>Olá, {{ nome }}!</p>
```

**Observações sobre Data Binding:**

- O Data Binding facilita a comunicação entre o modelo e a interface do usuário, tornando o desenvolvimento mais intuitivo.
- O Two-Way Binding é particularmente útil para formulários e inputs.
- O `v-bind` e o `v-on` podem ser combinados para criar interações dinâmicas.

---

## Class e Style Binding no Vue.js

Além do data binding tradicional, o Vue.js oferece funcionalidades adicionais para manipular classes CSS e estilos diretamente no template.

### Class Binding

O Class Binding permite adicionar ou remover classes CSS dinamicamente com base em valores do modelo.

Exemplo:

```html
<button :class="{ 'botao-destaque': isDestaque }">Clique aqui</button>
```

Neste exemplo, a classe CSS **'botao-destaque'** será adicionada ao botão se a propriedade **isDestaque** for verdadeira.

Também é possível passar um array de classes:

```html
<button :class="['classe1', 'classe2']">Clique aqui</button>
```

### Style Binding

O Style Binding permite definir estilos CSS dinamicamente com base nos valores do modelo.

Exemplo:

```html
<p :style="{ color: corTexto }">Este texto possui uma cor dinâmica</p>
```

Neste exemplo, a cor do parágrafo será definida pelo valor da propriedade **corTexto**.

**Aplicando condições com Class e Style Binding**

Podemos usar expressões ternárias para aplicar classes e estilos dinamicamente.

Exemplo:

```html
<button :class="isDestaque ? 'botao-destaque' : ''">Clique aqui</button>
```

Ou usar múltiplas condições:

```html
<button :class="{ 'botao-destaque': isDestaque && !isDesabilitado }">Clique aqui</button>
```

**Class e Style Binding em Two-Way Binding**

Podemos combinar `v-model` com `class` para criar estilos dinâmicos baseados em entrada do usuário.

```html
<input v-model="classeCSS" :class="classeCSS">
```

---

## Prática

Aqui está a sugestão para a prática:

**Tema do Projeto**: Lista de Tarefas

**Descrição**: Criar os templates para uma aplicação de Lista de Tarefas (*To-Do List*), onde os usuários podem adicionar, marcar como concluídas e remover tarefas. A aplicação deve ser desenvolvida usando o Vue.js, aplicando os conceitos aprendidos na aula.

**Requisitos**:

- A aplicação deve ter um componente principal que representará a Lista de Tarefas.
- O template deve permitir gerenciar as tarefas (adicionar, marcar como concluída, remover).
- Use [BootStrapCDN](https://getbootstrap.com.br/docs/4.1/getting-started/introduction/) para estilizar o projeto.

