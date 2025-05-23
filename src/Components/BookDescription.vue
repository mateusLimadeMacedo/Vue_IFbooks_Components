<template>
  <div id="dois">
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

</template>

<style scuped>
#dois {
  display: flex;
  padding: 3vw 6vw 3vw 4vw;
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




.text-p {
  display: flex;
  align-items: end;
  justify-content: end;
  width: 70%;
  color: black;

}

</style>