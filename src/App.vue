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
function totalValor() {
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
  <div class="flexbox">

    <ul class="">
      <div class="card">
        <div class=" card-body row align-items-start m-2 p-2 ">
          <li class="col" v-for="(item, index) in item" :key="item.id">
            <p class="list-group-item">{{ item.nome }}</p>
            <p>Preco: {{ item.preco }}</p>
            <p>quantidade: {{ item.quantidade }}</p>
            <button class="btn btn-primary aad" @click="incrementar(index)">Aumentar</button>
            <button class="btn btn-primary aad" @click="descrementar(index)">Remover</button>
            <button class="btn btn-primary aad" @click="addCarrinho(item)">Adicionar</button>
          </li>
        </div>
      </div>
    </ul>
    <hr>


    
  </div>
  <ul class="oie">
      <div class="md-3">
        <h1>Carrinho</h1>
        <ul class="carrinho list-group">
          <li class="list-group-item" v-for="(item, index) in carrinho" :key="index">{{ item.nome }}
            <p> valor: {{ (item.preco) }} Preço</p>
            <p>Quant: {{ item.quantidade }}</p>
            <button class="btn btn-primary"  id="remove" @click="remover(index)">remover item</button>
            <p class="letraTotal">Preço total: {{ (item.totalItem) }}</p>


          </li>
          <button class="btn btn-primary" @click="limpaCarrinho()">Limpar carrinho</button>
        </ul>
        
      </div>
    </ul>
</template>

<style scoped>
.produtos {
  margin: 20px;
  width: calc(33.33% - 40px);
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 10px;
  background-color: #fff;
  border: 1px solid #ccc;
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.2);
  border-radius: 5px;
  transition: transform 0.2s ease-in-out;
}
.oie {
  display: flex;
  position: relative;
  justify-content: center;
  align-items: center;
}
.produtos:hover {
  transform: translateY(-5px);
}

.produtos p {
  margin: 0;
  text-align: center;
}

.produtos p:nth-of-type(1) {
  font-size: 1.2rem;
  font-weight: bold;
  margin-bottom: 10px;
}

.produtos p:nth-of-type(2) {
  font-size: 1rem;
  margin-bottom: 10px;
}

.produtos p:nth-of-type(3) {
  font-size: 0.8rem;
  margin-bottom: 10px;
}

.produtos button {
  height: 30px;
  width: 100%;
  border-radius: 5px;
  background-color: #4CAF50;
  color: #fff;
  font-size: 0.9rem;
  cursor: pointer;
  border: none;
  margin-top: auto;
}

.produtos button:hover {
  background-color: #3e8e41;
}

.aad {
  width: 200px;
  margin: 5px;
}

.list-group {
  column-gap: 10px;

  justify-content: space-between;
  align-items: center;

}

.teste {
  flex-wrap: wrap;
  justify-content: center;
  height: 1000px;
}

.flexbox{
    place-items: center;
}

.col {
  text-decoration: none;
}

.carrinho {
  justify-content: center;
  align-items: center;
}

.md-3 {
  justify-content: center;
  align-items: center;
}

</style>
