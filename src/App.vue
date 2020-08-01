<template>
  <div id="app">

    <forms/>

  </div>
</template>

<script>

import forms from './components/form'

export default {
  name: 'App',
  components: {
    forms
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
