<script setup>
import { ref } from 'vue'

const item = ref([
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

function incrementar(index) {
    item.value[index].quantidade++
  }
  function descrementar(index) {
    item.value[index].quantidade--
  }
  let valortotal = ref(0)

  let carrinho = ref([])
function addCarrinho(item) {
  carrinho.value.push({
    codigo: item.id,
    nome: item.nome,
    preco: item.preco,
    quantidade: item.quantidade,
    totalItem: item.preco * item.quantidade
  })
  totalValor()
  item.quantidade = 1
}
function totalValor(){
  for (let contador = 0; contador < carrinho.value.length; contador++) {
    valortotal.value = valortotal.value + carrinho.value[contador].totalItem  
  }
}
function limpaCarrinho() {
  carrinho.value = []
}
function remover(index) {
  carrinho.value.splice(index, 1)
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
        <button @click="addCarrinho(item)">Adicionar</button>
      </li>
    </ul>
    <hr>
    <li v-for="item in carrinhos">
        <p>Item: {{ item.name }}</p>

        <p>Preco: {{ item.price }}</p>
        <p>ID: {{ item.id }}</p>
    </li>
  </div>

  <ul>
    <div class="">
    <h1>Carrinho</h1> 
    <ul>
      <li v-for="(item, index) in carrinho" :key="index">{{ item.nome }} 
      <p> valor: {{(item.preco) }} Preço</p>
    <p>Quant: {{ item.quantidade }}</p>
    <button id="remove" @click="remover(index)">remover item</button>  
    <p class="letraTotal">Preço total: {{ (item.totalItem) }}</p>
    
   
      </li>
    </ul>
    <button @click="limpaCarrinho()">limpar carrinho</button>
  </div>
</ul>
</template>

<style scoped>


ul{
  display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-template-rows: 5fr 5fr;
}
</style>
