<script setup>
const props = defineProps(['tarefas']);
</script>

<template>
    <ul v-if="tarefas.length > 0" class="list-group mt-4">
      <li class="list-group-item" v-for="tarefa in props.tarefas">
        <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada" type="checkbox" :id="tarefa.titulo">
        <label :class="{done: tarefa.finalizada}" class="ms-3" :for="tarefa.titulo">
          {{ tarefa.titulo }}
        </label>
      </li>
    </ul>
    <span class="list-group mt-4" v-else>Não há nenhuma tarefa</span>
</template>

<style scoped>
  .done {
     text-decoration: line-through;
     color: grey
  }
</style>