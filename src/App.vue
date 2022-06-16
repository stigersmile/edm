<template>
  <div id="app">
    <FormPage></FormPage>
    <TestPage> </TestPage>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import FormPage from './components/FormPage.vue'
import TestPage from './components/TestPage.vue'

export default {
  name: 'App',
  components: {
    FormPage,
    TestPage
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
