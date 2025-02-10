<template>
  <div class="container mt-5">
    <h1 class="text-center">Lista de Tarefas</h1>

    <!-- Campo de Entrada para Nova Tarefa -->
    <div class="input-group mb-3">
      <input type="text" class="form-control" placeholder="Nova tarefa" v-model="novaTarefa" @keyup.enter="adicionarTarefa">
      <div class="input-group-text">
        <button class="btn btn-primary" @click="adicionarTarefa">Adicionar</button>
      </div>
    </div>

    <!-- Lista de Tarefas -->
    <ul class="list-group">
      <li v-for="(tarefa, index) in tarefas" :key="index" class="list-group-item d-flex justify-content-between align-items-center">
        <span :class="{'text-decoration-line-through': tarefa.concluida}">{{ tarefa.nome }}</span>
        <div>
          <button class="btn btn-success btn-sm mr-2" @click="marcarConcluida(index)" v-if="!tarefa.concluida">Concluir</button>
          <button class="btn btn-danger btn-sm" @click="removerTarefa(index)">Remover</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      novaTarefa: '',
      tarefas: []
    }
  },
  methods: {
    // Método para adicionar nova tarefa
    adicionarTarefa() {
      if (this.novaTarefa.trim() === '') {
        return;
      }
      this.tarefas.push({ nome: this.novaTarefa, concluida: false });
      this.novaTarefa = ''; // Limpa o campo de entrada
    },
    // Método para marcar tarefa como concluída
    marcarConcluida(index) {
      this.tarefas[index].concluida = true;
    },
    // Método para remover tarefa
    removerTarefa(index) {
      this.tarefas.splice(index, 1);
    }
  }
}
</script>

<style scoped>
/* Estilos personalizados (se necessário) */
</style>
