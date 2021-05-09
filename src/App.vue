<template>
  <dg-header />
  <dg-main />
</template>

<script>
import dgHeader from './components/dgHeader.vue';
import dgMain from './components/dgMain.vue';

export default {

  name: 'App',
  components: {
    dgHeader,
    dgMain,
  },
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
