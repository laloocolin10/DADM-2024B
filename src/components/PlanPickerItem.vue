<template>
  <div @click="selectPlan" class="plan">
    <div class="description">
      <span class="title">
        {{ name }} {{ isSelected ? '🌟' : '' }}
      </span>
    </div>
  </div>
</template>

<script setup>
// Importamos la función para crear una propiedad computada
import { computed } from 'vue';

// Definimos las props usando la macro
const props = defineProps({
  name: {
    type: String,
    required: true
  },
  selectedPlan: String // Prop adicional para comparar
});

// Definimos los eventos emitidos por el componente
const emit = defineEmits(['select']);

// Función que emite el evento para seleccionar el plan
const selectPlan = () => {
  emit('select', props.name);
};

// Propiedad computada para verificar si el plan ha sido seleccionado
const isSelected = computed(() => {
  return props.name === props.selectedPlan;
});
</script>

<style scoped>
.plan {
  /* Agrega tus estilos aquí */
}
</style>
