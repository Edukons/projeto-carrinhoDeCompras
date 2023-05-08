<script setup>
import { ref } from 'vue'

     /*const items = ref([
        { id: 1, name: '', details: { description: '', price: 17.90 } },
        { id: 2, name: '', details: { description: '', price: 9.90 } },
        { id: 3, name: '', details: { description: '', price: 27.50 } },
        { id: 4, name: '', details: { description: '', price: 39.90 } },
        { id: 5, name: '', details: { description: '', price: 29.99 } },
        { id: 6, name: '', details: { description: '', price: 7.90 } },
        { id: 7, name: '', details: { description: 'Item 3 description', price: 30.00 } },
        { id: 8, name: '', details: { description: 'Item 3 description', price: 30.00 } },
        { id: 9, name: '', details: { description: 'Item 3 description', price: 30.00 } },
        { id: 10, name: '', details: { description: 'Item 3 description', price: 30.00 } },

  ])*/const item = ref([
{ 
        id: 1,
        nome: 'Caderno 10 matérias',
        preco: 17.50,
        quantidade: 0,
    },
    {
        id: 2,
        nome: 'Caderno 1 matéria',
        preco: 9.90,
        quantidade: 0,
    },
    {
        id: 3,
        nome: 'Lápis de cor Faber-Castell',
        preco: 27.90,
        quantidade: 0,
    },
    {
        id: 4,
        nome: 'EcoLápis SuperSoft Faber-Castell',
        preco: 39.99,
        quantidade: 0,
    },
    {
        id: 5,
        nome: 'Kit escolar Faber-Castell',
        preco: 28.90,
        quantidade: 0,
    },
    {
        id: 6,
        nome: 'Kit caneta esferográfica Faber-Castell',
        preco: 7.90,
        quantidade: 0,
    },
    {
        id: 7,
        nome: 'Coleção Lettering Básico Faber-Castell',
        preco: 55.90,
        quantidade: 0,
    },
    {
        id: 8,
        nome: 'Marca Texto Textliner Pastel 46 Faber-Castell',
        preco: 59.90,
        quantidade: 0,
    },
    {
        id: 9,
        nome: 'Lápis Grafite EcoLápis Castell 9000 2B/6B/8B Sextavado Faber-Castell',
        preco: 10.60,
        quantidade: 0,
    },
    {
        id: 10,
        nome: 'Apontador com depósito Pôster Estampas Sortidas, Faber-Castell',
        preco: 6.90,
        quantidade: 0,
    }
])

  const carrinhos = ref([
{
        id: 10,
        nome: '',
        preco: 19.55,
        quantidade: 0,
    }
])

function incrementar(index) {
    item.value[index].quantidade++
  }
  function descrementar(index) {
    item.value[index].quantidade--
  }
  
  function adicionar(index) {
    carrinhos.value.push(item.value)
    carrinhos.value = ''
  }
  
</script>

<template>
  <div class="row">
    <ul>
      <li class="lista" v-for="(item, index) in item" :key="item.id">
        <p>Item: {{ item.nome }}</p>
        <p>Preco: {{ item.preco }}</p>
        <p>ID: {{ item.id }}</p>        
        <p>quantidade: {{ item.quantidade }}</p>
        <button @click="incrementar(index)">+</button>
        <button @click="descrementar(index)">-</button>
        <button @click="adicionar">Adicionar</button>
      </li>
    </ul>
    <hr>
    <li v-for="item in carrinhos">
        <p>Item: {{ item.name }}</p>

        <p>Preco: {{ item.price }}</p>
        <p>ID: {{ item.id }}</p>
    </li>
  </div>
</template>

<style scoped>

</style>
