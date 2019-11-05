<template>
  <div id="app">
    <GitHub />
  </div>
</template>

<script>
  import GitHub from './components/GitHub'

  export default {
    name: 'app',
    components: {
      GitHub
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>