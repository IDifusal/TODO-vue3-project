<template>
  <h1>App tareas</h1>
  <TareaFormulario />
  <Tarea-item v-for="(tarea, index) in tareas" :key="index" :tarea="tarea" />
  <div v-if="tareas.length === 0" class="alert alert-dark mt-3">Sin tareas</div>
  <p>{{ tareas }}</p>
</template>
<script>
import { ref, provide, watchEffect } from "vue";
import TareaFormulario from "../components/TareaForm.vue";
import TareaItem from "../components/TareaItem.vue";
export default {
  components: {
    TareaFormulario,
    TareaItem,
  },
  setup() {
    const tareas = ref([]);
    provide("tareas", tareas);

    if (localStorage.getItem("tareas")) {
      tareas.value = JSON.parse(localStorage.getItem("tareas"));
    }
    watchEffect(() => {
      localStorage.setItem("tareas", JSON.stringify(tareas.value));
    });
    return { tareas };
  },
};
</script>