<template>
  <div
    class="
      alert alert-warning
      mt-3
      d-flex
      justify-content-between
      align-items-center
    "
  >
    <p :class="{ tachado: tarea.estado }">{{ tarea.texto }}</p>
    <div>
      <i
        @click="modificarTarea(tarea.id)"
        class="fas fa-undo-alt mx-2 text-success"
        role="button"
        v-if="tarea.estado"
      ></i>
      <i
        @click="modificarTarea(tarea.id)"
        class="fas fa-check mx-2 text-success"
        role="button"
        v-else
      ></i
      ><i
        @click="eliminarTarea(tarea.id)"
        class="fas fa-minus-circle text-danger"
        role="button"
      ></i>
    </div>
  </div>
</template>
<script>
import { inject } from "@vue/runtime-core";
export default {
  props: {
    tarea: {
      type: Object,
      required: true,
    },
  },
  setup() {
    const tareas = inject("tareas");
    const eliminarTarea = (id) => {
      tareas.value = tareas.value.filter((item) => item.id != id);
    };
    const modificarTarea = (id) => {
      tareas.value = tareas.value.map((item) => {
        if (item.id === id) {
          item.estado = !item.estado;
        }
        return item;
      });
    };
    return { eliminarTarea, modificarTarea };
  },
};
</script>
<style scoped>
.tachado {
  text-decoration: line-through;
}
</style>