<script setup>
   import planItem from './components/plan-item.vue';
   import { ref } from 'vue';
   const plans = ref(['El cafetero', 'El Chelero', 'El intelectual']);
</script>

<template>
    
    <div class="plans">
          <plan-item v-for="plan in plans" :key="plan" :name="plan"/>
    </div>

</template>


<style scoped>

</style>