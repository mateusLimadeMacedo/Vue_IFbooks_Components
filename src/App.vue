<script setup>
import { reactive, ref } from 'vue';
import HeaderComponent from './Components/HeaderComponent.vue';
import BookDescription from './Components/BookDescription.vue';
import StatesComponent from './Components/StatesComponent.vue';
import BookBuy from './Components/BookBuy.vue';
import BooleanoComponent from './Components/BooleanoComponent.vue';


const booleano = ref(false);

const produtos = reactive([
  {
    id: 1,
    titulo: 'Chain of Iron: Volume 2',
    autor: 'Cassandra Clare',
    preco: 23.24,
    quantidade: 1,
    capa: '/imgs/chain of torn.jpeg',
    precoSoma: 23.24,
  },
  {
    id: 2,
    titulo: 'Chain of Thorn: Volume 2',
    autor: 'Cassandra Clare',
    preco: 23.24,
    quantidade: 1,
    capa: '/imgs/chai of torn vdd.jpeg',
    precoSoma: 23.24,
  },
  {
    id: 3,
    titulo: 'City of Fallen Angels',
    autor: 'Cassandra Clare',
    preco: 13.94,
    quantidade: 1,
    capa: '/imgs/city of.jpeg',
    precoSoma: 13.94,
  },
  {
    id: 4,
    titulo: 'Nona the Ninth',
    autor: 'Cassandra Clare',
    preco: 16.84,
    quantidade: 1,
    capa: '/imgs/clock work.jpeg',
    precoSoma: 16.84,
  },
  {
    id: 5,
    titulo: 'Harlem Shuffle',
    autor: 'Colson Whitehead',
    preco: 26.92,
    quantidade: 1,
    capa: '/imgs/parece um quadrino.jpeg',
    precoSoma: 26.92,
  },
  {
    id: 6,
    titulo: 'Two Old Women',
    autor: 'Velma Wallis',
    preco: 13.95,
    quantidade: 1,
    capa: '/imgs/women.jpeg',
    precoSoma: 13.95,
  },
  {
    id: 7,
    titulo: 'Carrie Soto Is Back',
    autor: 'Taylor Jenkins Reid',
    preco: 26.04,
    quantidade: 1,
    capa: '/imgs/carrie soto.jpeg',
    precoSoma: 26.04,
  },
  {
    id: 8,
    titulo: 'Book Lovers',
    autor: 'Emily Henry',
    preco: 15.81,
    quantidade: 1,
    capa: '/imgs/book lovers.png',
    precoSoma: 15.81,
  }
]);

const carrinho = reactive({
  items: [

  ],

  frete: 0,
  desconto: 0,
  total: 0,
});

function adicionar(produto) {
  let jaExiste = carrinho.items.find(item => item.id == produto.id);
  if (!jaExiste) {
    carrinho.items.push({...produto});
    carrinho.total += produto.preco
  }
  else {
    alert(`O livro já foi adicionado ao carrinho.`);
  }
}
function incrementar(item) {
  item.quantidade++
  item.precoSoma += item.preco
  carrinho.total += item.preco
}

function decrementar(item) {
  if (item.quantidade > 1) {
    item.quantidade--
    item.precoSoma -= item.preco
    carrinho.total -= item.preco
  }
  else {
    const pos = carrinho.items.findIndex(i => i.id == item.id);;
    carrinho.items.splice(pos, 1);
    carrinho.total -= item.preco;

  }
}
</script>

<template>
  <HeaderComponent @click-cart="booleano = true" @click-logo="booleano = false"/>


  <div v-if="booleano === false" id="dois">
    <BookDescription />


  </div>
    
    
 
  <div v-if="booleano === false" class="states">
    <StatesComponent />


  </div>
    

  <div v-if="booleano === false" class="books">
    <BookBuy :produtos="produtos" :carrinho="carrinho" @adicionar="adicionar"/>
    

  </div>

   <div class="booleano" v-if="(booleano === true)">
    <BooleanoComponent  :produtos="produtos"   :carrinho="carrinho"  @incrementar="incrementar"  @decrementar="decrementar"/>
   
  </div>

   <footer>
    <div class="maior">
      <div class="social">
        <p>IFbooks</p>
        <ul class="icons">
          <li>
            <a href=""><i class="fa-brands fa-square-facebook"></i></a>
          </li>
          <li>
            <a href=""><i class="fa-brands fa-instagram"></i></a>
          </li>
          <li>
            <a href=""><i class="fa-brands fa-square-twitter"></i></a>
          </li>
        </ul>
      </div>
      <div class="contato">
        <p class="con">Contato</p>
        <ul class="one">
          <li>
            <p><i class="fa-solid fa-hashtag"></i> +55 47 40045263</p>
          </li>
          <li>
            <p><i class="fa-solid fa-clock"></i> 8h às 23h - Seg a Sex</p>
          </li>
          <li>
            <p><i class="fa-solid fa-envelope"></i> contato@ifbooks.com</p>
          </li>
        </ul>
        <ul class="two">
          <li>
            <img src="/public/imgs/paypal.jpg" alt="PayPal">
          </li>
          <li>
            <img src="/public/imgs/MasterCard-Logo-1979 1.png" alt="MasterCard">
          </li>
          <li>
            <img src="/public/imgs/Visa.png" alt="Visa">
          </li>
        </ul>
      </div>
    </div>
    <div class="direitos">
      <p>© Alguns direitos reservados. IFbooks 2025.</p>
    </div>
  </footer>
  </template>

<style scoped>
div {
  display: flex;
}

div ul {
  display: flex;
  text-decoration: none;
  list-style-type: none;
}



.img {
  display: flex;
  flex-direction: column;
  width: 50%;

}

.img img {
  width: 65%;
  height: 50%;
}









/*=================================================================================Footer==============================================================*/

footer {
  background-color: #27ae60;

}

footer .maior {
  padding: 3vw 0 2vw 0;
  display: flex;
  justify-content: space-between;
  border-bottom: #d8d8d8 solid 2px;
}

.social {
  display: flex;
  flex-direction: column;
  margin-left: 8vw;
}

.social p {
  font-size: 1.3rem;
  color: white;
  margin-bottom: 1vw;
  font-weight: 300;
}

.social .icons {
  padding-left: 0;
  display: flex;
  justify-content: space-between;
}

.social .icons li i {
  color: white;
  font-size: 2.5rem;
  margin-right: 1vw;
}

.contato {
  display: flex;
  flex-direction: column;
  margin-right: 8vw;
  text-align: left;
}

.contato .con {
  font-size: 1.3rem;
  color: white;
  margin-bottom: 1.2vw;
  font-weight: 400;

}

.contato ul {
  padding-left: 0;

}

.contato .one {
  display: flex;
  flex-direction: column;
  margin-bottom: 4vw;
}

.contato .one li p {
  color: rgb(236, 236, 236);
  font-size: 1.1rem;
  margin-bottom: 0.8vw;
}

.contato .one li p i {
  margin-right: 0.5vw;
}

.direitos {
  display: flex;
  justify-content: center;
  padding: 1vw;
  font-size: 1.2rem;
  color: rgb(219, 219, 219);
}

.two {
  display: flex;
  justify-content: space-between;
  margin-bottom: 1vw;
}

.two li img {
  width: 57px;
  border-radius: 4px;
}
/*==============================================================================Carrinho=================================================================*/

</style>
