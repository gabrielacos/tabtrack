<template>
<v-laytout column>
  <v-flex xs6 offset-xs3>
    <div class= "white elevation-2">
      <v-toolbar flat dense class="cyan" dark>
        <v-toolbar-title>Login</v-toolbar-title>
      </v-toolbar>
  <div class="pl-4 pr-4 pb-2 pt-2">
    <h1>Login</h1>
    <v-text-field
    type="email"
    name="email"
    placeholder="email"
    v-model="email"/>
    <br>
    <v-text-field
    type=""
    name="password"
    placeholder="password"
    v-model="password"/>
    <br>
    <div class="error" v-html="error"></div>
    <br>
    <v-btn class="cyan white--text" @click="login">Login</v-btn>
  </div>
    </div>
  </v-flex>
</v-laytout>
</template>

<script>
import AuthenticationService from '@/services/AuthenticationService'
export default {
  data () {
    return {
      email: '',
      password: '',
      error: null
    }
  },
  methods: {
    async login () {
      try {
        await AuthenticationService.login({
          email: this.email,
          password: this.password
        })
      } catch (error) {
        this.error = error.response.data.error
      }
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.error{
  color:"red";
}
</style>
