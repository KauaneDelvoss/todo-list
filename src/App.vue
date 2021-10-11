<template>
  <div class="container">
    <h2>{{ titulo }}</h2>
    <div class="input-group">
      <input
        type="text"
        class="form-control"
        @keyup.enter="adicionarTarefa()"
        v-model="novaTarefa"
      />
      <span class="input-group-btn">
        <button @click="adicionarTarefa()" class="btn btn-success">
          Adicionar
        </button>
      </span>
    </div>
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
    <p>
      <em> Total de tarefas : </em> <span> {{ totalTarefas }} </span>
    </p>
    <p>
      <em> Tarefas concluídas : </em> <span> {{ totalTarefasConcluidas }}</span>
    </p>

    <footer>
      <hr />
      <em>Altere aqui o título da lista de tarefas</em>
      <input type="text" v-model="titulo" />
    </footer>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      titulo: "Minhas Tarefas",
      tarefas: [
        { titulo: "Estudar", checked: false },
        { titulo: "Ler", checked: false },
        { titulo: "Lavar louça", checked: false },
      ],
      novaTarefa: "",
    };
  },
  methods: {
    adicionarTarefa() {
      this.tarefas.push({
        titulo: this.novaTarefa,
        checked: false,
      });
      this.novaTarefa = "";
    },
  },
  computed: {
    totalTarefas() {
      return this.tarefas.length;
    },
    totalTarefasConcluidas() {
      return this.tarefas.filter((tarefa) => tarefa.checked).length;
    },
  },
};
</script>

<style>
.container {
  width: 60%;
  margin: 20px auto 0px auto;
}
.removed {
  color: grey;
}

.removed label {
  text-decoration: line-through;
}

ul li {
  list-style-type: none;
  margin: 5px;
}
</style>