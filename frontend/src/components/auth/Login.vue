<template>
  <b-container class="text-center">
    <h2>Login</h2>
    <b-form @submit="login">
      <b-form-input
        v-model="email"
        type="text"
        placeholder="Emailaddresse..."
        name="email" /><br>
      <b-form-input
        v-model="password"
        placeholder="Passwort..."
        type="password"
        name="password" /><br>
      <b-button type="primary">Login</b-button>
    </b-form>
    <p class="mt-4">Noch nicht registriert? <router-link to="register">Jetzt registrieren</router-link></p>
  </b-container>
</template>

<script>
import router from '../../router'
export default {
  data () {
    return {
      email: '',
      password: ''
    }
  },
  name: 'Login',
  methods: {
    login: (e) => {
      e.preventDefault()
      this.$store.dispatch('login', {email: this.email, password: this.password})
        .then(() => router.push('/'))
        .catch(err => console.log(err))
    }
  }
}
</script>
