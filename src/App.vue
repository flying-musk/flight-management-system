<template>
  <div id="app">
    <FlightManagementSystem />
  </div>
</template>

<script>
import FlightManagementSystem from './components/FlightManagementSystem.vue';
export default {
  name: 'App',
  components: { FlightManagementSystem },
};
</script>

<style lang="scss">
body {
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
}
</style>
