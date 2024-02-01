<template>
    <div id="LoginForm">
      <div>
        <form v-on:submit.prevent="conected">
        <h1>{{ title }}</h1>
        <p>Remplissez ce formulaire pour vous connecter.</p>
        <hr />

        <label for="email">
          <b>Email</b>
        </label>
        <input
          type="text"
          placeholder="Entrez votre courriel"
          id="email"
          name="email"
          required
          v-model="email"
        />
        <label for="psw"><b>Mot de passe</b></label>
        <input
          type="password"
          placeholder="Entrez votre mot de passe"
          id="psw"
          name="psw"
          required
          v-model="password"
        />
        <p><button type="submit" >Se connecter</button></p>
      </form>
      </div>
    </div>
</template>

<script>
export default {
  name: 'LoginForm',
  data(){
    return {
      email: '',
      password:'',
      loggedIn: false,
    }
  },
  props:{
    title: String
  },
  methods: {
    conected(){
      if(this.email === "email@bidon.fr" && this.password === "movie") {
        this.loggedIn = true
        this.$emit('loggedIn', this.loggedIn)
      }
    },
  }
}
</script>