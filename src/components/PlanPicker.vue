<script setup>
import { ref } from 'vue';
import PlanPickerItem from './PlanPickerItem.vue';
   const plans = ref(['El cafetero', 'El Chelero', 'El intelectual']);
   const selectPlan = (name) =>
   {
    console.log(name);
   };
</script>

<template>

    <div class="plans">
          <PlanPickerItem 
          v-for="plan in plans" 
          :key="plan" 
          :name="plan"
          @select="selectPlan"/>
    </div>

</template>


<style scoped>

</style>