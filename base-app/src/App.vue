<template>
  <div id="app">\
    <h1>teste</h1>
    <Home/>
  </div>
</template>


<script>
// import Home from 'vueGithubList/Home';
export default {
 components: {
   Home: async () => await import('vueGithubList/Home'),
 }
}
</script>