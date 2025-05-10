<script setup>
import { reactive, ref } from 'vue';


const booleano = ref(false);

const produtos = reactive([
  {
    id: 1,
    titulo: 'Chain of Iron: Volume 2',
    autor: 'Cassandra Clare',
    preco: 23.24,
    quantidade: 1,
    capa: 'public/imgs/chain of torn.jpeg',
    precoSoma: 23.24,
  },
  {
    id: 2,
    titulo: 'Chain of Thorn: Volume 2',
    autor: 'Cassandra Clare',
    preco: 23.24,
    quantidade: 1,
    capa: 'public/imgs/chai of torn vdd.jpeg',
    precoSoma: 23.24,
  },
  {
    id: 3,
    titulo: 'City of Fallen Angels',
    autor: 'Cassandra Clare',
    preco: 13.94,
    quantidade: 1,
    capa: 'public/imgs/city of.jpeg',
    precoSoma: 13.94,
  },
  {
    id: 4,
    titulo: 'Nona the Ninth',
    autor: 'Cassandra Clare',
    preco: 16.84,
    quantidade: 1,
    capa: 'public/imgs/clock work.jpeg',
    precoSoma: 16.84,
  },
  {
    id: 5,
    titulo: 'Harlem Shuffle',
    autor: 'Colson Whitehead',
    preco: 26.92,
    quantidade: 1,
    capa: 'public/imgs/parece um quadrino.jpeg',
    precoSoma: 26.92,
  },
  {
    id: 6,
    titulo: 'Two Old Women',
    autor: 'Velma Wallis',
    preco: 13.95,
    quantidade: 1,
    capa: 'public/imgs/women.jpeg',
    precoSoma: 13.95,
  },
  {
    id: 7,
    titulo: 'Carrie Soto Is Back',
    autor: 'Taylor Jenkins Reid',
    preco: 26.04,
    quantidade: 1,
    capa: 'public/imgs/carrie soto.jpeg',
    precoSoma: 26.04,
  },
  {
    id: 8,
    titulo: 'Book Lovers',
    autor: 'Emily Henry',
    preco: 15.81,
    quantidade: 1,
    capa: 'public/imgs/book lovers.png',
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
  <section id="um">
    <div id="primeiros">
      <a @click="booleano = false" >IFbooks</a>
      <p>
        Apreço a <br />
        leitura
      </p>
    </div>
    <div class="search">
      <input type="text" placeholder="Pesquisar" />
      <i class="fa-solid fa-magnifying-glass"></i>
    </div>
    <div id="termos">
      <nav>
        <ul>
          <li>
            <a href="#termos">Termos</a>
          </li>
          <li>
            <a href="#equipe">Equipe</a>
          </li>
          <li>
            <a href="#envio">Envio</a>
          </li>
          <li>
            <a href="#devolucoes">Devoluções</a>
          </li>
        </ul>
      </nav>
    </div>
    <div id="icones">
      <nav>
        <ul>
          <li>
            <button @click="booleano = true"><i class="fa-solid fa-cart-shopping"></i></button>
          </li>
          <li>
            <span><a href=""><i class="fa-solid fa-heart"></i></a></span>
          </li>
          <li>
            <a href=""><i class="fa-solid fa-user"></i></a>
          </li>
        </ul>
      </nav>
    </div>
  </section>


  <div v-if="booleano === false" id="dois">
    <div class="book-description">
      <h3>Autor de Abril</h3>
      <h1>Eric-Emanuel Schmitt</h1>
      <p>
        Eric-Emmanuel Schmitt has been awarded more than 20 literary prizes and distinctions, and in
        2001 he received the title of Chevalier des Arts et des Lettres. His books have been
        translated into over 40 languages.
      </p>
      <button>Acessar página do livro</button>
    </div>
    <div class="img">
      <div>
        <img src="/public/imgs/9ca5b51d70fa54350c0c18670357cf85.png" alt="Eric-Emanuel Schmitt book" />
      </div>
      <div class="text-p">
        <p>*within the stock limit</p>
      </div>
    </div>
  </div>
  <div v-if="booleano === false" class="states">
    <div>
      <i class="fa-solid fa-box"></i>
      <p>frete grátis para SC</p>
    </div>
    <div id="state-middle">
      <i class="fa-solid fa-star"></i>
      <p>Livros recomendados</p>
    </div>
    <div class="line">
      <i class="fa-solid fa-book-open"></i>
      <p>Mais vendidos</p>
    </div>
  </div>
  <div v-if="booleano === false" class="books">
    <h1>Lançamentos</h1>
    <div class="books-container">

      <div class="shop" v-for="produto in produtos" :key="produto.id">
        <img :src="produto.capa" alt="">
        <h3>{{ produto.titulo }}</h3>
        <p>{{ produto.autor }}</p>
        <div class="like">
          <p> {{ produto.preco.toLocaleString('pt-br', { style: 'currency', currency: 'BRL' }) }}</p>
          <button class="coracao" @click="favoritar"><i class="fa-solid fa-heart"></i></button>
        </div>

        <button @click="adicionar(produto)" class="comprar"><i class="fa-solid fa-cart-shopping"></i> Comprar</button>

      </div>
    </div>

  </div>

   <div class="booleano" v-if="(booleano === true)">
    <h3><Span>Carrinho</Span></h3>
    <div class="atributos">
      <p>Título</p>
      <p>Quantidade</p>
      <p>Subtotal</p>
    </div>

    <div class="itens" v-for="item in carrinho.items" :key="item.id">
      <div class="dados">
        <img :src="item.capa" alt="">
        <div class="coluna">
          <h3> {{ item.titulo }} </h3>
          <p id="autor"> {{ item.autor }} </p>
          <p id="preco"> {{ item.preco.toLocaleString('pt-br', { style: 'currency', currency: 'BRL' }) }}</p>
        </div>
      </div>
      <div class="quantidade">
        <button @click="decrementar(item)">-</button>
        <p>{{ item.quantidade }}</p>
        <button v-on:click="incrementar(item)">+</button>
      </div>
      <div class="preco_geral">
        <p>{{ item.precoSoma.toLocaleString('pt-br', { style: 'currency', currency: 'BRL' }) }}</p>
      </div>

    </div>

    <button @click="booleano = !booleano" class="voltar">Voltar para a loja</button>

    <div class="abaixo">

      <div class="cupom">
        <input type="text" placeholder="Código do cupom" />
        <button >Inserir Cupom</button>
      </div>

      <div class="total_compraT">
        <div class="total_compra">
        <h3>Total da Compra</h3>

        <div class="produtos">
          <p>Produtos:</p>
          <p>{{ carrinho.total.toLocaleString('pt-br', { style: 'currency', currency: 'BRL' }) }}</p>
        </div>

        <div class="frete">
          <p>Frete:</p>
          <p>Grátis</p>
        </div>

        <div class="total">
          <p>Total:</p>
          <p>{{ carrinho.total.toLocaleString('pt-br', { style: 'currency', currency: 'BRL' }) }}</p>
        </div>
      </div>
        <div id="button">

          <button>Ir para o pagamento</button>

        </div>


      </div>

    </div>
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
#um {
  padding: 1.1vw;
  display: flex;
  justify-content: space-around;
  align-items: center;
  border-bottom: #27ae60 solid 0.1rem;
}

div {
  display: flex;
}

#primeiros a {
  margin: 0 1vw 0 0;
  font-size: 1.1rem;
  text-decoration: none;
  color: black;
  cursor: pointer;
}

#primeiros p {
  color: #27ae60;
  font-size: 0.7rem;
  line-height: 1rem;
  padding-left: 1vw;
  border-left: #27ae60 solid 0.15rem;
}

div ul {
  display: flex;
  text-decoration: none;
  list-style-type: none;
}

#termos ul li a {
  display: flex;
  text-decoration: none;
  color: rgb(163, 161, 161);
  margin: 0 3vw 0 0;
}

#icones ul li a {
  margin: 0 1vw 0 1vw;
  text-decoration: none;
  color: #27ae60;
  font-size: 1.1rem;
}

#icones ul {
  align-items: center;
}

#icones ul li button {
  margin: 0 1vw 0 1vw;
  text-decoration: none;
  color: #27ae60;
  font-size: 1.1rem;
  border: none;
  background-color: white;
  cursor: pointer;
}

#icones ul li span {
  border-left: #27ae60 solid 0.15rem;
  border-right: #27ae60 solid 0.15rem;
}

.search input {
  font-size: 1.1rem;
  padding: 0.3vw 7vw 0.3vw 0.6vw;
  background-color: rgb(240, 237, 237);
  border: none;
  outline: 0;
}
.search input::placeholder {
  color: rgb(187, 184, 184);
  font-size: 0.9rem;
}
.search {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgb(240, 237, 237);
  padding-right: 10px;
}
.search i{
  color: #231F2D;
  cursor: pointer;
}
#dois {
  display: flex;
  padding: 6vw 0vw 4vw 12vw;
  justify-content: center;
  align-items: center;
}

.book-description {
  display: flex;
  flex-direction: column;
  padding: 20px;
  width: 70%;
}

#dois h3 {
  border: #27ae60 solid 0.1rem;
  border-radius: 0.3vw;
  padding: 0.5vw;
  display: flex;
  justify-content: center;
  align-items: center;
  color: #27ae60;
  width: 20%;
  margin-bottom: 1.5vw;
}
#dois h1 {
  font-size: 3.5rem;
  font-weight: bold;
  color: #382c2c;
}

.book-description p {
  width: 45%;
  font-size: 1.1rem;
  margin-top: 1.1vw;
  color: #4D4C4C;
}

#dois button {
  margin-top: 2.7vw;
  width: 30%;
  font-size: 1.1rem;
  padding: 0.85vw 1vw;
  background-color: #27ae60;
  color: white;
  border: none;
  border-radius: 4px;
  transition: background-color 0.15s ease-in-out;
}
#dois button:active{
  background-color: rgb(5, 107, 9);
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

.text-p {
  display: flex;
  align-items: end;
  justify-content: end;
  width: 70%;
  color: black;

}

.states {
  display: flex;
  justify-content: space-around;
  align-items: center;
  gap: 20px;
  padding: 100px;
  border-bottom: 1px #27ae60 solid;
  border-top: #27ae60 solid 1px;
}

.states div {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 20px;
  padding: 20px;
}

.states p,
.states i {
  font-size: 30px;
  font-weight: bold;
  color: #382c2c;
}

.states .line p {
  border-bottom: #382c2c solid 1px;
  padding-right: 2vw;
}

#state-middle {
  border-left: 1px solid;
  border-right: 1px solid;
  padding: 20px;
  width: 650px;
}

.books {
  padding: 100px;
  display: flex;
  gap: 20px;
  flex-direction: column;
}

.books h1 {
  font-size: 3rem;
  font-weight: bold;
  margin: 2vw 0 3.5vw 2.5vw;
  color: #382c2c;
}

.books-container {
  display: flex;
  justify-content: space-around;
  margin-bottom: 6vw;
  flex-wrap: wrap;
  gap: 10px;
}

.books-container .shop {
  width: 22%;
  display: flex;
  flex-direction: column;
  margin-bottom: 4vw;
}

.books-container .shop img {
  width: 100%;
  border-radius: 3px;
}

.coracao {
  color: #27ae60;
  cursor: pointer;
}

.books-container .shop h3 {
  margin-top: 1vw;
  font-size: 1.6rem;
  color: #382c2c;
  font-weight: bold;

}

.books-container .shop p {
  color: #4f4c57;
  margin-bottom: 0.6vw;
  font-size: 1.1rem;
}

.books-container .shop div p {
  font-size: 1.3rem;
  font-weight: bold;
  color: #382c2c;
}

.books-container .shop .comprar {
  border: none;
  background-color: #27ae60;
  color: white;
  padding: 0.8vw 1vw;
  border-radius: 3px;
  font-size: 1rem;
  margin-top: 1.3vw;
  cursor: pointer;
  transition: background-color 0.2s ease-in-out;
}
.books-container .shop .comprar:active{
  background-color: rgb(5, 107, 9);
}

.books-container .shop img {
  height: 100%;
}

.books-container .shop .like {
  display: flex;
  justify-content: space-between;
  align-items: center;
  text-align: center;
}

.books-container .shop .like button {
  background-color: white;
  color: #27ae60;
  border: none;
  padding: 0 1vw 0 0;
  font-size: 1.6rem;
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
.booleano {
  padding: 3vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin: 0 5vw;
}

.booleano h3 span {
  color: #27ae60;
  font-size: 2.5rem;
  font-weight: 500;


}

.booleano .atributos {
  display: flex;
  justify-content: space-between;
  margin: 5vw 0 0 0;
  font-size: 1.4rem;
  padding-bottom: 1vw;
  border-bottom: #27ae60 solid 1px;
  color: black;
  font-weight: 600;
}

.dados, .quantidade, .preco_geral{
  width: 33%;

}

.preco_geral{
  display: flex;
  justify-content: end;
}

.itens {
  padding: 3vw 1vw;
  display: flex;
  border-bottom: #b6b5b5 solid 2px;
  align-items: center;
  justify-content: space-between;

}

.itens .dados img {
  width: 150px;
  height: 220px;
  border-radius: 3px;
  margin-right: 3vw;
}

.itens .coluna {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.itens .coluna h3 {
  font-weight: 900;
  font-size: 1.5rem;
  max-height: 40px;
  max-width: 25vw;
  word-wrap: break-word;
  text-overflow: ellipsis;
  overflow: hidden;
  white-space: nowrap;
  color: #382C2C;


}

.itens .coluna #autor {
  margin: 0.8vw 0 0.8vw 0;
  font-size: 1.1rem;
  color: #4F4C57;
}

.itens .coluna #preco {
  font-weight: 700;
  font-size: 1.5rem;
  color: #382C2C;
}

.itens .quantidade {
  display: flex;
  justify-content: center;
  align-items: center;
  border: #000000 solid 1px;
  height: 56px;
  width: 124px;
}

.itens .quantidade button {
  border: none;
  background-color: white;
  font-size: 1.5rem;
}

.itens .quantidade p {
  font-size: 1.5rem;
  padding: 0 10px;
  color: black;
}

.preco_geral p {
  font-size: 1.6rem;
  font-weight: 600;
  color: #382c2c;
}
.booleano .voltar{
  margin: 3vw 0 6vw;
  width: 15%;
  padding: 0.9vw 1.3vw;
  border: #000000 solid 1px;
  font-size: 1.1rem;
  background-color: white;
  border-radius: 4px;
  font-weight: 500;

}
.cupom input{
  font-size: 1.1rem;
  padding: 0.2vw 1.6vw;
  background-color: rgb(255, 255, 255);
  border: black solid 1px;
  outline: 0;
  border-radius: 4px;
  margin-right: 1vw;
  height: 16%;
}

.cupom input::placeholder{
  color: rgb(136, 136, 136);
  font-size: 1.1rem;
}
.cupom{
  display: flex;

}
.cupom button{
  font-size: 1.1rem;
  padding: 0.2vw 3vw;
  background-color: #27ae60;
  border-radius: 4px;
  margin-right: 1vw;
  height: 16%;
  color: white;
  border: none;
   transition: background-color 0.15s ease-in-out;
}
.cupom button:active{
  background-color: rgb(5, 107, 9);

}
.abaixo{
  display: flex;
  justify-content: space-between;

}
.total_compra {
  display: flex;
  flex-direction: column;
  padding: 1.5vw 1.5vw 0;
  width: 430px;
  justify-content: center;
  color: black;



}
.total_compraT {
  display: flex;
  flex-direction: column;
  border: #000000 solid 1px;
  padding: 1vw;
  justify-content: center;
  align-items: center;
  border-radius: 4px;


}
.total_compra h3{
  font-size: 1.5rem;
  margin-bottom: 1vw;

}
.produtos,
.frete,
.total{
  display: flex;
  justify-content: space-between;
  border-bottom: rgb(185, 185, 185) solid 1px;
  padding: 0.8vw 0vw;

}
.total{
  border: none;
}
.total_compraT button{
  font-size: 1.1rem;
  background-color: #27ae60;
  border-radius: 4px;
  margin-right: 1vw;
  color: white;
  border: none;
  text-align: center;
  padding: 17px 60px;
   transition: background-color 0.15s ease-in-out;
}
.total_compraT button:active{
  background-color: rgb(5, 107, 9);

}




#button{
  text-align: center;
  align-items: center;
}

button {
  cursor: pointer;
}
</style>
