<template>
  <div class="app">
    <div class="nav">
      <router-link v-if="authenticated" to="/login" v-on:click.native="logout()" replace>Logout</router-link>
    </div>
    <router-view @authenticated="setAuthenticated" />
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      authenticated: false,
      admin: {
        username: "david",
        password: "keiser"
      }
    }
  },
  
  mounted() {
    if (!this.authenticated) {
      this.$router.replace({ name: "login"});
    }
  },
  methods: {
    setAuthenticated(status) {
      this.authenticated = status;
    },
    logout(){
      this.authenticated = false;
    }
  }
}
</script>

<style>
  body {
    background-color: #f0f0f0;
  }
  h1 {
    padding: 0;
    margin-top: 0;
  }
  .app {
    width: 1024px;
    margin: auto;
  }
</style>
