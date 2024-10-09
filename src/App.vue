<script setup>
import { ref } from 'vue'
const header = ref('App Lista de compras')
//---items---
//Item.Model
const items = ref([
  { id: 1, label: '1 Nutrileche' },
  { id: 2, label: '1 Aceite de Bebe' },
  { id: 3, label: '1 lata de atún' },
  { id: 4, label: '1 Nutella' }
])

// Items-Method
const saveItem = (items) => {
  items.value.push({ id: items.value.length + 1, label: newItem.value })
  //Clean the input
  newItem.value = ''
}

// Visualizacion formulario
const newItem = ref('')
const newItemHighPriority = ref(false)
const editing = ref(true)
const activeteEdition = (activate) => {
  editing.value = activate
}
</script>

<template>
  <div class="header">
    <h1>
      <i class="material-icons shopping-cart-icon"> local_mall </i>
      {{ header }}
    </h1>
    <button v-if="editing" class="btn" @click="activeteEdition(false)">Cancelar</button>
    <button v-else class="btn btn-primary" @click="activeteEdition(true)">Agregar</button>
  </div>

  <!--colocando un hiperlink visto en clase-
  <a v-bind:href="newItem === '' ? 'https://www.google.com' : 'https://' + newItem" target="_blank">
    {{ newItem === '' ? '🖇Link' : newItem }}
  </a>
-->

  <!-- Agrupando Entradas de usuario -->
  <form class="add-item form" v-if="editing" v-on:submit.prevent="saveItem">
    <!-- Entrada de texto -->
    <input type="text" placeholder="Add Item" v-model.trim="newItem" />
    <!-- Radio Buttons -->
    <label><input type="checkbox" v-model="newItemHighPriority" />Alta Prioridad</label>
    <!-- Boton -->
    <button :disabled="newItem.length===0" class="btn btn-primary">Salvar Articulo</button>
  </form>
  <!-- Lista -->
  <ul>
    <li v-for="{ id, label } in items" v-bind:key="id">𓅓 {{ label }}</li>
  </ul>
  <p v-if="items.length === 0">🥀 NO HAY ELEMENTOS EN LA LISTA 🥀</p>
</template>

<style scoped>
.shopping-cart-icon {
  font-size: 2rem; /* Adjust the font-size value as per your desired size*/
}
</style>
