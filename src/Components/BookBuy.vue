<script setup>
defineProps(['produtos', 'carrinho'])
defineEmits(['adicionar'])


</script>



<template>
<div class="books">
        <h1>Lançamentos</h1>
    <div class="books-container">

      <div class="shop" v-for="produto in produtos" :key="produto.id">
        <img :src="produto.capa" alt="">
        <h3>{{ produto.titulo }}</h3>
        <p>{{ produto.autor }}</p>
        <div class="like">
          <p> {{ produto.preco.toLocaleString('pt-br', { style: 'currency', currency: 'BRL' }) }}</p>
          <button class="coracao"><i class="fa-solid fa-heart"></i></button>
        </div>

        <button @click="$emit('adicionar', book)" class="comprar"><i class="fa-solid fa-cart-shopping"></i> Comprar</button>

      </div>
    </div>

</div>
</template>

<style scoped>
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



</style>