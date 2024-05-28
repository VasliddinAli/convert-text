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
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
