<template>
  <div class="input-group">
    <!-- <input
      type="text"
      class="form-control"
      @keyup.enter="adicionarTarefa()"
      v-model="novaTarefa"
    /> -->

    <span class="input-group-btn">
      <!-- <button @click="adicionarTarefa()" class="btn btn-success"> -->
      <!--   Adicionar
      </button> -->
      <b-field label="O que você precisa lembrar de fazer hoje?">
        <b-input
          placeholder="Nova Tarefa"
          rounded
          v-model="novaTarefa"
          size="is-small"
        ></b-input>
      </b-field>
      <b-button
        focused
        @click="adicionarTarefa()"
        size="is-small"
        rounded="true"
        >Adicionar</b-button
      >
      <hr />
    </span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      novaTarefa: "",
    };
  },
  methods: {
    adicionarTarefa() {
      this.$emit("adicionarTarefa", this.novaTarefa);
      this.novaTarefa = "";
    },
  },
};
</script>


<style>
</style>