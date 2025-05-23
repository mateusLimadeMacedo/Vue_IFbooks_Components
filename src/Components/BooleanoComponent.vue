<script setup>
defineProps(['carrinho', 'produtos'])
defineEmits(['incrementar', 'decrementar'])


</script>



<template>
<div class="booleano">
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
        <button @click="$emit('decrementar')">-</button>
        <p>{{ item.quantidade }}</p>
        <button @click="$emit('incrementar')">+</button>
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

</template>

<style scoped>
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
