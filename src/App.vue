<script setup>
import { ref } from 'vue'

const item = ref([
  {
    id: 1,
    nome: 'Caderno 10 matérias',
    preco: 'R$17.50',
    quantidade: 0,
    img: 'https://img.kalunga.com.br/fotosdeprodutos/140158d.jpg'
  },
  {
    id: 2,
    nome: 'Caderno 1 matéria',
    preco: 'R$9.90',
    quantidade: 0,
    img: 'https://m.media-amazon.com/images/I/41+qb5G9XuL._AC_SX522_.jpg'
  },
  {
    id: 3,
    nome: 'Lápis de cor Faber-Castell',
    preco: 'R$27.90',
    quantidade: 0,
    img: 'https://m.media-amazon.com/images/I/71+yZoIMoIL._AC_SX522_.jpg'
  },
  {
    id: 4,
    nome: 'EcoLápis SuperSoft Faber-Castell',
    preco: 'R$39.99',
    quantidade: 0,
    img: 'https://m.media-amazon.com/images/I/71YZTAGiG0L._AC_SX522_.jpg'
  },
  {
    id: 5,
    nome: 'Kit escolar Faber-Castell',
    preco: 'R$28.90',
    quantidade: 0,
    img: 'https://m.media-amazon.com/images/I/41duoaoOOvL._AC_SL1000_.jpg'
  },
  {
    id: 6,
    nome: 'Kit caneta esferográfica Faber-Castell',
    preco: 'R$7.90',
    quantidade: 0,
    img: 'https://images.tcdn.com.br/img/img_prod/1106500/caneta_esferografica_faber_castell_1_0_trilux_com_3_unidades_3605_1_4cc65777baef90bc8ac2df89661b84d8.jpg'
  },
  {
    id: 7,
    nome: 'Coleção Lettering Básico Faber-Castell',
    preco:'R$55.90' ,
    quantidade: 0,
    img: 'https://m.media-amazon.com/images/I/61i8x-LqjaL._AC_SX522_.jpg'
  },
  {
    id: 8,
    nome: 'Marca Texto Textliner Pastel 46 Faber-Castell',
    preco: 'R$59.90',
    quantidade: 0,
    img: 'https://m.media-amazon.com/images/I/61rYedzsFXL._AC_SX522_.jpg'
  },
  {
    id: 9,
    nome: 'Lápis Grafite EcoLápis Castell 9000 2B/6B/8B Sextavado Faber-Castell',
    preco: 'R$10.60',
    quantidade: 0,
    img: 'https://img.kalunga.com.br/fotosdeprodutos/410681d.jpg'
  },
  {
    id: 10,
    nome: 'Apontador com depósito Pôster Estampas Sortidas, Faber-Castell',
    preco: 'R$6.90',
    quantidade: 0,
    img: 'https://www.artebazar.com.br/pub/media/catalog/product/cache/3537fff87e70f6889f529633c676f8c1/a/p/apontador_com_deposito_poster_faber_castell.webp'
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
    valortotal= item.quantidade*item.preco
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
<h1 class="h1">Papelaria Kons</h1>
    <ul class="">
      <div class="card">
        <div class=" card-body row align-items-start m-2 p-2 ">
          <li class="col" v-for="(item, index) in item" :key="item.id">
            <img :src="item.img" width="210" height="270">
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
      <div class="md-3 ">
        <h1 class="h1C">Carrinho🛒</h1>
        <ul class="carrinho list-group">
          <li class="list-group-item" v-for="(item, index) in carrinho" :key="index">{{ item.nome }}
            <p> Preço: {{ item.preco }} </p>
            <p>Quant: {{ item.quantidade }}</p>
            <p class="letraTotal">Preço total: {{ (valortotal) }}</p>
            <button class="btn btn-primary"  id="remove" @click="remover(index)">remover item</button>
          </li>
          <button class="btn btn-primary " @click="limpaCarrinho()">Limpar carrinho</button>
        </ul>
        
      </div>
    </ul>
</template>

<style scoped>
.h1{
  text-align: center;
  color: #4CAF50;
  text-shadow:1px 2px #2c2a2a;
  background-color: rgb(138, 138, 116);
  border-radius: 10px;
  height: 60px;
}
.h1c{
  text-align: center;
  color: #4CAF50;
  text-shadow:1px 2px #2c2a2a;
  background-color: rgb(138, 138, 116);
  border-radius: 10px;
  height: 120px;
}
.produtos {
  margin: 20px;
  width: calc(33.33% - 40px);
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 10px;
  background-color: #494242;
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
button{
  background-color: #3e8e41;
  color: #ccc;
}

</style>
