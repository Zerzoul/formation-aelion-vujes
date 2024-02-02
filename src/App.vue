<template>
  <div id="app">
    <LoginForm v-if="!loggedIn" title="Authentification" @loggedIn="setLoggedIn"/>
    <SearchFilms v-if="loggedIn" />
  </div>
</template>

<script>
import LoginForm from './components/LoginForm.vue'
import SearchFilms from './components/SearchFilms.vue';

export default {
  name: 'App',
  components: {
    LoginForm,
    SearchFilms
  },

  data (){
    return{
      loggedIn: true,
    }
  },

  methods: {
    setLoggedIn(value) {
      this.loggedIn = value
    }
  }
}
</script>

<style>
@import "./assets/base.css";
</style>
