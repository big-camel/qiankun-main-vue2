<template>
  <div id="app">
    <micro-app name="header" :title="title" />
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <input v-model="title" />
    <router-view />
  </div>
</template>
<script>
import MicroApp from './MicroApp.vue'
export default {
  name: 'App',
  data () {
    return {
      title: 'Welcome to Your Vue.js App'
    }
  },
  components: {
    MicroApp
  }
}
</script>
<style lang="less">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
