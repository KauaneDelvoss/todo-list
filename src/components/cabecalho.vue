
<template>
  <b-navbar>
    <template #brand>
      <b-navbar-item tag="router-link" :to="{ path: '/' }"> </b-navbar-item>
    </template>
    <template #start>
      <b-navbar-item href="#"> {{ valor }} </b-navbar-item>
      <b-navbar-item
        href="https://www.google.com/intl/pt-BR/calendar/about/"
        target="_blank"
      >
        Calendário
      </b-navbar-item>
      <b-navbar-dropdown label="Perfil">
        <b-navbar-item href="#"> Configurações </b-navbar-item>
        <b-navbar-item href="#"> Ajuda </b-navbar-item>
      </b-navbar-dropdown>
    </template>
    <header>{{ valor }}</header>
    <template #end>
      <b-navbar-item tag="div">
        <div class="buttons">
          <a class="button is-primary">
            <strong>Sign up</strong>
          </a>
          <a class="button is-light"> Log in </a>
        </div>
      </b-navbar-item>
    </template>
  </b-navbar>
</template>

<script>
export default {
  props: ["valor"],
};
</script>

<style>
</style>