<!-- 
nome repo: vite-breaking-bad
Descrizione:
Create un nuovo progetto utilizzando Vite e Vue 3 e definite i componenti necessari per strutturare il layout come da screenshot allegato.
Al caricamento della pagina, effettuate una chiama ajax all’API di Breaking Bad: https://www.breakingbadapi.com/api/characters
e con i dati restituiti, stampate una card per ogni personaggio.
Usate lo store, e potete strutturare l’app come visto questa mattina insieme.
Bonus:
Creare un componente loader da visualizzare fintantoché i risultati non sono pronti. 
-->


<script>
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <div id="cont">
    <div id="titolo">
      <div class="logo">
        <img
          src="https://w7.pngwing.com/pngs/88/896/png-transparent-rick-and-morty-text-overlay-rick-sanchez-the-art-of-rick-and-morty-rick-and-morty-season-3-the-rickshank-rickdemption-animated-series-others-television-blue-comics.png"
          alt="">
      </div>
      <h1>Rick and Morty Api</h1>
    </div>
    <div class="fascia">

      <div class="console">
        <div class="input">


          <div class="categorie">
            select category

            <i class="fa-solid fa-chevron-down"></i>
          </div>

        </div>
        <div class="finestra">

        </div>
      </div>
    </div>
    <HelloWorld />
  </div>
</template>

<style lang="scss" scoped>
@use './style/general.scss';




#cont {
  background-color: #323c48;
  display: flex;
  flex-direction: column;
  min-width: 100vw;
  min-height: 100vh;
}

#titolo {
  padding: 10px;
  display: flex;
  align-items: center;
  // background-color: brown;

  h1 {
    margin: 0 20px;
    color: white;
  }
}

.logo {
  // width: 50px;
  height: 50px;
  background-color: red;
  display: flex;
  align-items: center;
  justify-content: center;
  // overflow: hidden;

  img {
    width: auto;
    height: 100%;
  }
}

.fascia {
  // height: 100%;

  background-color: aqua;
  display: flex;
  align-items: center;
  justify-content: center;
}

.console {
  width: 600px;
  height: 400px;
  display: flex;
  flex-direction: column;
  // align-items: center;
  background-color: rgb(255, 170, 127);

  .input {
    padding: 10px;

    .categorie {
      background-color: #fefefd;
      border: 1px solid #d2d6da;
      padding: 3px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      width: 100px;
      font-size: 10px;
      color: rgb(102, 102, 102);
      border-radius: 4px;

      i {
        font-size: 6px;
      }
    }
  }
}

.finestra {
  width: 100%;
  height: 100%;
  // overflow: scroll;
  background-color: rgb(255, 255, 255);
}
</style>
