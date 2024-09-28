<script setup>
import { ref } from 'vue'
//modelo
const header = ref('App lista de compras')
const items = ref([
  { id: '0', label: 'Aceite' },
  { id: '1', label: 'Papel de baño' },
  { id: '2', label: '1 cheve' },
  { id: '3', label: '1 Pañal' },
  { id: '4', label: '1 Nutella' }
])
//realizado en clase
const newItem = ref('')
const newItemPriority = ref('low')

</script>

<template>
  <h1>
    <i class="material-icons shopping-cart-icon">local_mall</i>
    {{ header }}
  </h1>
   <!--Realizado en clase -->
  <input v-model="newItem" type="next" placeholder="Agregar Articulo" /> {{ newItem }}
  <!--Radio Buttons-->
  <label>
    <input type="radio" value="low" v-model="newItemPriority" />
    Baja
  </label>

  <label>
    <input type="radio" value="high" v-model="newItemPriority" />
    Alta
  </label>

  <!--Reto form -->
  <form v-on:submit.prevent="items.push({ id: items.length + 1, label: newItem })" class="add-item fomr"> 
    <button
      class="btn btn-primary">
      Salvar el articulo
    </button>
  </form>

  {{ newItemPriority == 'low' ? '🧊' : '🔥' }}
  <ul>
    <li v-for="item in items" :key="item.id">🛍️ {{ item.label }}</li>
  </ul>
</template>




<style scoped>
.shopping-cart-icon {
  font-size: 2rem;
}
</style>
