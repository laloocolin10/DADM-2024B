<script setup>
import { ref } from 'vue';
import PlanPickerItem from './PlanPickerItem.vue';

// Creando una referencia reactiva para almacenar el plan seleccionado
const selectedPlan = ref(null);
const plans = ref(['El cafetero', 'El Chelero', 'El intelectual']);

// Función para seleccionar un plan
const selectPlan = (name) => {
  // Almacenar el plan seleccionado
  selectedPlan.value = name;
};
</script>

<template>
  <div class="plans">
    <PlanPickerItem 
      v-for="plan in plans" 
      :key="plan" 
      :name="plan"
      @select="selectPlan"
      :selected-plan="selectedPlan.value"
    />
  </div>
  <p>Plan seleccionado: {{ selectedPlan.value }}</p>
</template>

<style scoped>
/* Agrega tus estilos aquí */
</style>
