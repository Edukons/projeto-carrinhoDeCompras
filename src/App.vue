<script setup>
     const items = [
        { id: 1, name: 'caderno1', details: { description: 'Caderno 10 matérias', price: 17.90 } },
        { id: 2, name: 'caderno2', details: { description: 'Caderno 1 matéria', price: 9.90 } },
        { id: 3, name: 'lapisDeCor', details: { description: 'Lápis de cor Faber-Castell', price: 27.50 } },
        { id: 4, name: 'ecoLapis', details: { description: 'EcoLápis SuperSoft Faber-Castell', price: 39.90 } },
        { id: 5, name: 'kitEscolar', details: { description: 'Kit escolar Faber-Castell', price: 29.99 } },
        { id: 6, name: 'kitCaneta', details: { description: 'kit caneta esferográfica Faber-Castell', price: 7.90 } },
        { id: 7, name: 'Item 7', details: { description: 'Item 3 description', price: 30.00 } },
        { id: 8, name: 'Item 8', details: { description: 'Item 3 description', price: 30.00 } },
        { id: 9, name: 'Item 9', details: { description: 'Item 3 description', price: 30.00 } },
        { id: 10, name: 'Item 10', details: { description: 'Item 3 description', price: 30.00 } },

  ]
</script>

<template>
    <ul>
    <li v-for="item in items" :key="item.id">
      <p>Nome: {{ item.name }}</p>
      <p>Detalhes</p>
      <p v-for="(value, key) in item.details" :key="key">{{ key }}: {{ value }}</p>
    </li>
  </ul>
</template>

<style scoped>

</style>
