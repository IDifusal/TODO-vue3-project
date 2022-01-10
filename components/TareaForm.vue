<template>
  <div class="text-center">
    <h2>Agregar Tarea</h2>
    <form @submit.prevent="agregarTarea">
      <input type="text" name="" v-model.trim="text" />
      <button class="btn btn-primary d-block m-auto" type="submit">
        Agregar tarea
      </button>
    </form>
  </div>
</template>
<script>
import { inject, ref } from "vue";
export default {
  setup() {
    const text = ref("");
    const tareas = inject("tareas");

    const agregarTarea = () => {
      if (text.value === "") {
        return console.log("texto vacio");
      }
      const tarea = {
        texto: text.value,
        estado: false,
        id: Date.now(),
      };
      tareas.value.push(tarea);
      text.value = "";
    };

    return { text, agregarTarea };
  },
};
</script>