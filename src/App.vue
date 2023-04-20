<template>
  <div id="app">
   <song-list></song-list>
   
  </div>
</template>

<script>
//imported the Songlist and the components

import SongList from '@/components/SongList.vue';
export default {
  name: 'App',
  components: {
   
   SongList,
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
