<template>
  <div :id="`micro-app-${name}`">
  </div>
</template>
<script>
import { loadMicroApp } from 'qiankun';

export default {
  name: 'MicroApp',
  data() {
    return {
      microApp: null,
    };
  },
  props: {
    name: String,
    title: String,
  },
  watch: {
    'title': {
      handler(newValue, oldValue) {
        if(!this.microApp) return
        this.microApp.update({
          props: {
            title: newValue,
          }
        })
        console.log('props', newValue, oldValue);
      },
      immediate: true,
      deep: true
    }
  },
  mounted() {
    this.microApp = loadMicroApp({
      name: this.name,
      entry: '//localhost:8000',
      container: `#micro-app-${this.name}`,
      props: {
        title: this.title
      }
    });
    console.log(this.microApp)
  },
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
