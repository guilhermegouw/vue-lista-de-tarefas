<template>
  <h1 v-text="titulo"></h1>
  <h2>{{ subtitulo }}</h2>

  <input v-model="novaTarefa" type="text" placeholder="Adicione uma tarefa">
  <button @click="adicionarTarefa">Adicionar</button>
  <button @click="limparTarefas" :disabled="tarefas.length==0">Limpar tudo</button>

  <div v-if="tarefas.length <=0">
    <p>Nenhuma tarefa cadastrada</p>
  </div>
  <div v-if="tarefas.length > 0">
    <p>Existem {{ tarefas.length }} tarefas cadastradas</p>
    <ul>
        <li v-for="(tarefa, id) in tarefas" :key="id"> {{ tarefa}} </li>
    </ul>
  </div>
</template>

<script>

export default {
  name: 'lv-tarefas',
  data() {
      return {
          titulo: 'Listagem de tarefas',
          subtitulo: 'Defina uma descrição para a tarefa',
          novaTarefa: '',
          tarefas: []
      }
  },
  methods: {
      adicionarTarefa() {
          if (this.novaTarefa.trim() !== '') {
              this.tarefas.push(this.novaTarefa);
              this.novaTarefa = '';
          }
        },
      limparTarefas() {
          this.tarefas = [];
      }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
