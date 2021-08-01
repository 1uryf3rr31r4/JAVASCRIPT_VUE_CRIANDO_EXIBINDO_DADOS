<template>
  <div id="app">
    <div>
      <h1 v-once v-text="titulo"></h1>
      <h2>{{subtitulo}}</h2>
      <input v-bind:disable="tarefas.length == 0" v-bind:style="estilo" v-model="subtitulo" type="text" placeholder="Descrição">
    </div>
    <div v-if="tarefas.length <= 0">
      Não há tarefas
    </div>
    <div v-if="tarefas.length > 0">
      Existem {{tarefas.length}} tarefas
      <ul>
        <li v-for="tarefa in tarefas">{{tarefa}}</li>
      </ul>
    </div>
    <button v-on:click="tarefas = []">Limpar</button>
  </div>
</template>

<script>
export default {
  name: 'lv-tarefas',
  data () {
    return {
      titulo: 'Listagem de Tarefas',
      subtitulo: 'Defina uma Descrição',
      tarefas: [],
      estilo: "text-align: center"
    }
  },
  mounted (){
    setTimeout(() => {
      this.titulo = "Novo Título"
      this.tarefas = [ 'tarefa 1', 'tarefa 2', 'tarefa 3']
      }, 2000)
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
