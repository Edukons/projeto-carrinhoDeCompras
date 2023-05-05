<script setup>
     const items = [
        { id: 1, name: 'Item 1', details: { description: 'Item 1 description', price: 10.00 } },
        { id: 2, name: 'Item 2', details: { description: 'Item 2 description', price: 20.00 } },
        { id: 3, name: 'Item 3', details: { description: 'Item 3 description', price: 30.00 } },
        { id: 4, name: 'Item 4', details: { description: 'Item 3 description', price: 30.00 } },
        { id: 5, name: 'Item 5', details: { description: 'Item 3 description', price: 30.00 } },
        { id: 6, name: 'Item 6', details: { description: 'Item 3 description', price: 30.00 } },
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
