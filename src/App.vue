<template>
  <div id="app">
    <h1>TODO-Liste</h1>
    <EntryList/>
  </div>
</template>

<script>

import EntryList from './components/EntryList'

export default {
  name: 'App',
  components: {
    EntryList
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
body{
  background-color: rgb(228, 242, 248);
}
</style>
