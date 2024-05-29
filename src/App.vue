<template>
  <div id="app">
    <ShuffleConverter />
  </div>
</template>

<script>
import ShuffleConverter from './views/ShuffleConverter.vue';

export default {
  name: 'App',
  components: {
    ShuffleConverter
  }
};
</script>

<style>
body{
    background-color: #121212;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #dddddd;
}
</style>
