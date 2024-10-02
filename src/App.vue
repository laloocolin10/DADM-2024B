<script setup>
import { ref } from 'vue'
// Modelo
const header = ref('App lista de compras')
//items
//item-model
const items = ref([
  { id: '0', label: '1 pepino' },
  { id: '1', label: '1 Aceite para bebe' },
  { id: '2', label: '1 barra de mantequilla' },
  { id: '3', label: '1 nutella' }
]);
//item-Method
const saveItem = () =>
{
   items.value.push({id: items.value.length + 1, label: newItem.value});
   //clean the imput-Limpia el imput
   newItem.value = '';
};

const newItem = ref('')
const newItemHighPriority = ref(false)
</script>

<template>
  <h1>
    <i class="material-icons shopping-cart-icon">local_mall</i>
    {{ header }}
  </h1>

  <form
    v-on:submit.prevent="saveItem"
  >
    <input v-model="newItem" type="text" placeholder="Agregar un articulo" />
    <!--Caja de seleccion de Prioridad-->

    <label>
      <input type="checkbox" v-model="newItemHighPriority" />
      Alta Prioridad
    </label>

    <!--Boton-->
    <button class="btn btn-primary">Salvar Articulo</button>
  </form>

  {{ newItemHighPriority }}
  <!-- Lista -->
  <ul>
    <li v-for="item in items" :key="item.id">𓅓 {{ item.label }}</li>
  </ul>
</template>

<style scoped>
.shopping-cart-icon {
  font-size: 2rem;
}
</style>
