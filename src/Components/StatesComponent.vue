<template>
<div class="states">
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
  
</template>

<style scoped>









div.states {
  display: flex;
  justify-content: space-around;
  align-items: center;
  gap: 20px;
  padding: 100px 0;
  border-bottom: 1px #27ae60 solid;
  border-top: #27ae60 solid 1px;
  width: 100%;
}

div.states div {
  display: flex;
  justify-content: center;
  align-items: center;
  
  padding: 20px;
}

div.states p,
div.states i {
  font-size: 30px;
  font-weight: bold;
  color: #382c2c;
}

div.states .line p {
  border-bottom: #382c2c solid 1px;
  padding-right: 2vw;
}

#state-middle {
  border-left: 1px solid;
  border-right: 1px solid;
  padding: 20px;
  width: 650px;
}


</style>