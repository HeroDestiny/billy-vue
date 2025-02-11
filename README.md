## Vue.js Diretivas

As Diretivas são uma parte fundamental do Vue.js, permitindo estender a sintaxe HTML para **adicionar comportamentos** personalizados aos elementos da página.

Existem três tipos principais de diretivas no Vue.js:

- Diretivas de Atributo
- Diretivas de Estrutura
- Diretivas Personalizadas

### Diretivas de Atributo

As Diretivas de Atributo são usadas para alterar o comportamento de elementos HTML existentes, adicionando ou modificando atributos e estilos dinamicamente. Elas são aplicadas como atributos de elementos no template.

Exemplos:

```html
<!-- Diretiva de Atributo v-bind:style -->
<p :style="{ background: isBlue ? 'blue' : 'red' }">Eu sou uma diretiva de atributo</p>
```

```html
<!-- Diretiva de Atributo v-bind:class -->
<p :class="{ 'fundo-verde': isFlag, 'fundo-azul': !isFlag }">Diretiva de Atributo - v-bind:class</p>
```

As diretivas **v-bind:style** e **v-bind:class** são usadas para alterar o estilo e as classes de qualquer elemento do DOM com base em alguma condição.

[Documentação Oficial Vue - v-bind](https://vuejs.org/guide/essentials/class-and-style.html)

### Diretivas de Estrutura

As Diretivas de Estrutura são usadas para manipular a estrutura do DOM, adicionando ou removendo elementos HTML do template.

#### Diretiva v-if

Exemplo:

```html
<!-- Diretiva de Estrutura -->
<div v-if="mostrarElemento">Este elemento só será exibido se mostrarElemento for verdadeiro.</div>
```

Aqui, **'v-if'** é uma Diretiva de Estrutura que adiciona ou remove o elemento `<div>` com base no valor de **'mostrarElemento'**.

[Documentação Oficial Vue - v-if](https://vuejs.org/guide/essentials/conditional.html)

#### Diretiva v-for

A diretiva **v-for** permite iterar sobre uma coleção de elementos e renderizá-los no template.

Exemplo:

```html
<div v-for="(item, index) in itens" :key="index">Item {{ index }}: {{ item }}</div>
```

Aqui estamos iterando sobre uma coleção chamada **itens**, e para cada item na coleção, o template renderizará um novo **<div>** contendo o valor do item.

[Documentação Oficial Vue - v-for](https://vuejs.org/guide/essentials/list.html)

#### Diretiva v-show

A diretiva **v-show** é usada para mostrar ou ocultar um elemento com base em uma condição, mas sem removê-lo do DOM (diferente do v-if).

```html
<p v-show="mostrarTexto">Este parágrafo será exibido se mostrarTexto for verdadeiro.</p>
```

[Documentação Oficial Vue - v-show](https://vuejs.org/guide/essentials/conditional.html#v-show)

#### Diretiva v-switch (Vue 3)

O Vue 3 permite criar lógica de troca de elementos com o `v-if`, `v-else-if` e `v-else`, funcionando de maneira semelhante ao switch-case.

```html
<div>
  <p v-if="opcao === 'A'">Você escolheu a opção A</p>
  <p v-else-if="opcao === 'B'">Você escolheu a opção B</p>
  <p v-else-if="opcao === 'C'">Você escolheu a opção C</p>
  <p v-else>Escolha uma opção válida (A, B ou C).</p>
</div>
```

[Documentação Oficial Vue - Condicionais](https://vuejs.org/guide/essentials/conditional.html)

### Diretivas Personalizadas

Você também pode criar suas próprias Diretivas personalizadas no Vue.js usando a API `directive`.

Exemplo de uma Diretiva Personalizada para destacar um elemento ao passar o mouse:

```javascript
app.directive('destaque', {
  beforeMount(el, binding) {
    el.style.backgroundColor = binding.value || 'yellow';
    el.addEventListener('mouseenter', () => {
      el.style.backgroundColor = 'lightgreen';
    });
    el.addEventListener('mouseleave', () => {
      el.style.backgroundColor = binding.value || 'yellow';
    });
  }
});
```

Uso no template:

```html
<p v-destaque="'lightblue'">Este parágrafo será destacado ao passar o mouse.</p>
```

[Documentação Oficial Vue - Diretivas Personalizadas](https://vuejs.org/guide/reusability/custom-directives.html)

**Considerações Finais**

As Diretivas são um recurso poderoso do Vue.js, permitindo criar comportamentos personalizados e reutilizáveis no template. Ao combiná-las com recursos como Data Binding e Componentes, você pode criar aplicações web mais interativas e dinâmicas.

## Prática

Aqui está a sugestão para a prática:

**Tema do Projeto:** Lista de Tarefas

**Descrição:** Criar uma aplicação de Lista de Tarefas (*To-Do List*), onde os usuários podem adicionar, marcar como concluídas e remover tarefas. A aplicação deve ser desenvolvida usando Vue.js, aplicando os conceitos aprendidos na aula.

**Requisitos:**

- Incluir os conceitos de diretivas (`v-if`, `v-for`, `v-bind:class`) na aplicação.

