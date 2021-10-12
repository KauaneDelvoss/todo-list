<template>
  <ul>
    <li
      v-for="(tarefa, index) in tarefas"
      :key="index"
      :class="{ removed: tarefa.checked }"
    >
      <input v-model="tarefa.checked" type="checkbox" />
      <label for="">
        {{ tarefa.titulo }}
      </label>
    </li>
  </ul>
</template>

<script>
export default {
  props: ["tarefas"],
};
</script>

<style>
</style>