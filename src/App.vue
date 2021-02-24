<template>
  <div>
    <Navbar 
      :showLogin="showLogin" 
      :showRegistro="showRegistro" 
      :pagina="mensagem" />
    <Login @login="login" v-if="paginaAtual === 'paginaLogin'"/>
    <Registro v-if="paginaAtual === 'paginaRegistro'"/>
    <h1 v-if="!auth && paginaAtual === 'paginaHome'">Página de casa</h1>
    <PaginaPrincipal v-if="auth && paginaAtual === 'paginaHome'"/>
  </div>
</template>

<script>
import Login from './components/Login.vue'
import Navbar from './components/Navbar.vue'
import Registro from './components/Registro.vue'
import PaginaPrincipal from './components/PaginaPrincipal.vue'

export default {
  name: 'App',
  components: {
    Navbar,
    Login,
    Registro,
    PaginaPrincipal,
  },
  data() {
    return {
      paginaAtual: 'paginaHome',
      mensagem: "Bem vindo",
      showLogin: true,
      showRegistro: true,
      auth:false,
      accessToken: null,
      refreshToken: null,
    }
  },
  methods: {
    teste: function() {
      this.showLogin = false
    },
    clickPaginaLogin: function () {
      this.paginaAtual = 'paginaLogin'
      this.mensagem = 'Página de login'
      this.showLogin = false
      this.showRegistro = true
    },
    clickPaginaHome: function () {
      this.paginaAtual = 'paginaHome'
      this.mensagem = 'Bem vindo'
      this.showLogin = true
      this.showRegistro = true
    },
    clickPaginaRegistro: function () {
      this.paginaAtual = 'paginaRegistro'
      this.mensagem = 'Registro de usuário'
      this.showLogin = true
      this.showRegistro = false
    },
    login: function (data) {
      this.showLogin = false
      this.showRegistro = false
      this.mensagem = data.accessToken
      this.auth = true
      this.accessToken = data.accessToken
      this.refreshToken = data.refreshToken
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
