<template>
  <tarea-app />
</template>

<script>
import TareaApp from "../components/TareaApp.vue";
export default {
  name: "App",
  components: {
    TareaApp,
  },
};
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
