<template>
  <div id="app">
    <h1  class="title">Lista de Usuários do Github</h1>
    <Home/>
  </div>
</template>


<script>
export default {
 components: {
   Home: async () => await import('vueGithubList/Home'),
 }
}
</script>

<style scoped>
#app {
  padding: 50px 50px;
}

.title {
  text-align: center;
  font: lighter;
  color: #f24783;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}

</style>