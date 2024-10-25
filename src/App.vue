<script setup>
import { ref } from 'vue'
const header = ref('App Lista de compras')

//---items---
const items = ref([
  { id: 1, label: '1 Nutrileche', purchased: false, highPriority: true },
  { id: 2, label: '1 Aceite de Bebe', purchased: true, highPriority: true },
  { id: 3, label: '1 lata de atún', purchased: false, highPriority: false },
  { id: 4, label: '1 Nutella', purchased: true, highPriority: true }
])

// Visualización formulario
const newItem = ref('')
const newItemHighPriority = ref(false)
const editing = ref(true)

const activeteEdition = (activate) => {
  editing.value = activate
  if (!activate) { // Limpiar campos al cancelar la edición
    newItem.value = ''
    newItemHighPriority.value = false
  }
}

// Alternando estado de compra del item
const togglePurchased = (item) => {
  item.purchased = !item.purchased;
};

// Método para agregar nuevos elementos a la lista
const saveItem = () => {
  items.value.push({
    id: items.value.length + 1,
    label: newItem.value,
    highPriority: newItemHighPriority.value
  });
  // Reiniciando la entrada de texto
  newItem.value = "";
  newItemHighPriority.value = false;
};

// Función que alterna el valor de la variable editing
const doEdit = (edit) => {
  editing.value = edit;
  // Limpiando la entrada de texto
  newItem.value = "";
  newItemHighPriority.value = false;
};
</script>

<template>
  <div class="header">
    <h1>
      <i class="material-icons shopping-cart-icon">local_mall</i>
      {{ header }}
    </h1>
    <button v-if="editing" class="btn" @click="activeteEdition(false)">Cancelar</button>
    <button v-else class="btn btn-primary" @click="activeteEdition(true)">Agregar</button>
  </div>

  <form class="add-item form" v-if="editing" v-on:submit.prevent="saveItem">
    <input type="text" placeholder="Add Item" v-model.trim="newItem" />
    <label><input type="checkbox" v-model="newItemHighPriority" />Alta Prioridad</label>
    <button :disabled="newItem.length === 0" class="btn btn-primary">Salvar Articulo</button>
  </form>

  <ul>
    <li
      v-for="item in items"
      @click="togglePurchased(item)"
      v-bind:key="item.id"
      :class="{ strikeout: item.purchased, priority: item.highPriority }"
    >
      ⚜ {{ item.label }}
    </li>
  </ul>
  <p v-if="items.length === 0">🥀 No hay elementos en la lista</p>
</template>

<style scoped>
.shopping-cart-icon {
  font-size: 2rem; /* Adjust the font-size value as per your desired size*/
}
</style>
