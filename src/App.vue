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

</style>
