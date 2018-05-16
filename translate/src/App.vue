<template>
  <div id="app">

  </div>
</template>
<script>
  import TranslateForm from "./components/translateForm"
  import TranslateOutput from './components/translateForm'
  export default {
    name: 'App',
    components: {
      TranslateForm,
      TranslateOutput
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
