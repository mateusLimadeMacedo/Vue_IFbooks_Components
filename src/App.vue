<script setup>

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
</style>
