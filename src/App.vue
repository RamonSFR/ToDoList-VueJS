<script setup>
import { reactive } from 'vue';

const estado = reactive({
  tarefas: [
    {
      titulo: "Estudar ES6",
      finalizada: false,
    },
    {
      titulo: 'Estudar SASS',
      finalizada: false,
    },
    {
      titulo: 'Ir para a academia',
      finalizada: true,
    }
  ],
});

const getTarefasPendentes = () => {
  return estado.tarefas.filter(tarefa => !tarefa.finalizada);
}
</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-light rounded-3">
      <h1>Minhas Tarefas</h1>
      <p>Você possui {{ getTarefasPendentes().length }} tarefas pendentes</p>
    </header>
    <form>
      <div class="row">
        <div class="col">
          <input
            type="text" placeholder="Digite aqui a descrição da tarefa" class="form-control"/>
        </div>
        <div class="col-md-2">
          <button class="btn btn-primary" type="submit">Cadastrar</button>
        </div>
        <div class="col-md-2">
          <select class="form-control">
            <option value="todas">Todas as Tarefas</option>
            <option value="todas">Tarefas pendentes</option>
            <option value="todas">Tarefas finalizadas</option>
          </select>
        </div>
      </div>
    </form>
    <ul class="list-group mt-4">
      <li class="list-group-item" v-for="tarefa in estado.tarefas">
        <input :checked="tarefa.finalizada" type="checkbox" :id="tarefa.titulo">
        <label :class="{done: tarefa.finalizada}" class="ms-3" :for="tarefa.titulo">
          {{ tarefa.titulo }}
        </label>
      </li>
    </ul>
  </div>
</template>

<style scoped>
  .done {
     text-decoration: line-through;
  }
</style>
