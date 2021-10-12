<template>
  <section>
    <cabecalho :valor="titulo" />
    <div class="container">
      <adicionartarefa v-on:adicionarTarefa="adicionarTarefa" />
      <b-field label="Altere aqui o título da lista de tarefas!">
        <b-input
          type="text"
          v-model="titulo"
          size="is-small"
          rounded="true"
        ></b-input>
      </b-field>
      <hr />
      <listagem :tarefas="tarefas" />
      <hr />
      <p>
        <em> Total de tarefas : </em> <span> {{ totalTarefas }} </span>
      </p>
      <p>
        <em> Tarefas concluídas : </em>
        <span> {{ totalTarefasConcluidas }}</span>
      </p>

      <!-- <hr />
      <em>Altere aqui o título da lista de tarefas</em>
      <input type="text" v-model="titulo" /> -->
    </div>

    <rodape />
  </section>
</template>

<script>
import Vue from "vue";
import Buefy from "buefy";
import "buefy/dist/buefy.css";

Vue.use(Buefy);

import cabecalho from "@/components/cabecalho";
import rodape from "@/components/rodape";
import listagem from "@/components/listagem";
import adicionartarefa from "@/components/adicionartarefa";
export default {
  name: "App",
  components: { cabecalho, rodape, listagem, adicionartarefa },
  data() {
    return {
      titulo: "Minhas Tarefas",
      tarefas: [
        {
          titulo:
            "Atrasar quase um mês para entregar o trabalho de programação",
          checked: true,
        },
        { titulo: "Ver as notas do sigaa e se desesperar", checked: true },
        {
          titulo: "Implorar para o professor aceitar o trabalho",
          checked: true,
        },
        { titulo: "Aprender a usar Buefy", checked: false },
        {
          titulo: "Esperar que o trabalho não esteja simples demais",
          checked: true,
        },
      ],
    };
  },
  methods: {
    adicionarTarefa(novaTarefa) {
      this.tarefas.push({
        titulo: novaTarefa,
        checked: false,
      });
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
  width: 40%;
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
h2 {
  padding: 40px 0px 0px 0px;
}
</style>