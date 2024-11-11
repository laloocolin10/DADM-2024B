<template>
   <div @click="selectPlan" class="plan">
    <div class="description">
      <span class="title">
       {{ name }} {{  selected ? '🌟' : '' }} 
      </span>
    </div>
  </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  //usando macro para definir las props
  //defineProps(['name', 'planIcon']);
  const props = defineProps ({
    name: {
      type: String, 
      required: true
    }
});
//define event 
const emit = defineEmits(['select']);
//variable que permite recordar si el plan ha sido seleccionado 
const selected = ref(false);
//funcion que permite cambiar el estado de la variable
const selectPlan = () => {
  selected.value = true;
  //emitir evento del plan ha sido seleccionado 
  emit('select',props.name);
};
  </script>
  
  <style scoped>
  </style>