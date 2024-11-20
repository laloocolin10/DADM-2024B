<script setup>
  import PlanPickerItem from './PlanPickerItem.vue';
  import { ref, onMounted } from 'vue'; // Se debe usar onMounted, no mounted
  
  // Creando una referencia reactiva para almacenar el plan deseado 
  const selectedPlan = ref(null);
  const plans = ref(['El cafetero', 'El chelero', 'El intelectual']);
  
  const selectPlan = (name) => {
    // Almacenar el plan seleccionado
    selectedPlan.value = name; 
  };

  // Intentando obtener la referencia al elemento .plans
  console.log("Termina de ejecutar el script setup 🍾");
  
  // Registrando el hook onMounted (en lugar de mounted)
  onMounted(() => { // Cambié mounted por onMounted
    console.log("El componente PlanPicker se ha montado 🎉");
    console.log(document.querySelector('.plans'));
  });
</script>

<template>
  <div class="plans">
    <PlanPickerItem 
      v-for="plan in plans" 
      :key="plan"
      :name="plan"
      @select="selectPlan"
      :select-plan="selectedPlan"/>
  </div>
</template>

<style scoped>
</style>
