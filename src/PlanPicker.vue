<script setup>
   import PlanItem from './components/PlanItem.vue';
   import { ref } from 'vue';
   const plans = ref(['El cafetero', 'El Chelero', 'El intelectual']);
</script>

<template>

    <div class="plans">
          <PlanItem v-for="plan in plans" :key="plan" :name="plan"/>
    </div>

</template>


<style scoped>

</style>