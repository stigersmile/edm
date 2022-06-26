<template>
  <div id="app">
    <h1>EDM GENERATOR</h1>
    <FormPage></FormPage>
  </div>
</template>

<script>
import FormPage from './components/FormPage.vue'


export default {
  name: 'App',
  components: {
    FormPage,
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

* {
  box-sizing: border-box;
}

.header{
     display:flex;
     justify-content:space-between;
}

</style>
