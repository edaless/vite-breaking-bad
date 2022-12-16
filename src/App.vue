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
import Character from './components/Character.vue';
import { store } from './store.js';

export default {
  name: "App",
  components: {
    Character
  },
  data() {
    return {
      store
    }
  },

  methods: {
    getCharacters() {
      // chiamata api, avverrà appena finito di caricare il sito e 
      // quando si cambia il valore del menù a tendina
      let aggiunta = "";
      // stringa vuota che verrà aggiunta all'url dell'api,
      // non necessariamente riempita (se voglio tutti i personaggi)

      // se è stato richiesto uno status preciso aggiorno la AGGIUNTA con la stringa necessaria
      if (store.statusSelected !== "") {
        aggiunta = "?status=" + store.statusSelected;
      };

      axios
        .get(store.apiURL + aggiunta)
        .then(res => {
          store.characterList = res.data.results;
          // riempo l'array dello store con i risultati della chiamata api
        })
        .catch(err => {
          console.log("errori", err)
        });

    }
  },
  mounted() {
    this.getCharacters();
  }
}
</script>

<template>
  <div id="cont">
    <div id="titolo">
      <div class="logo">
        <img src="https://cdn.shopify.com/s/files/1/0014/2491/6549/collections/R_M_collab_logo.jpg?v=1623834373" alt="">
      </div>
      <h2>{{ store.titolo }}</h2>
    </div>
    <div class="fascia">

      <div class="console">
        <div class="input">

          <!-- menù a tendina che al click fa una nuova chiamata api -->
          <select id="status" v-model="store.statusSelected" @click="getCharacters()">
            <option value="">all</option>
            <option value="alive">alive</option>
            <option value="dead">dead</option>
            <option value="unknown">unknown</option>

          </select>

        </div>
        <div class="finestra">
          <div class="barra-risultati">
            Found {{ store.characterList.length }} characters
          </div>
          <!-- <Character :msg="store.characterList[0].name" /> -->
          <div id="lista-personaggi">
            <Character v-for="(character, index) in store.characterList" :msg="store.characterList[index]" />

          </div>


          <!-- 2:07 della registraz -->


        </div>
      </div>
    </div>


  </div>
</template>

<style lang="scss" scoped>
@use './style/general.scss';




#cont {
  background-color: #323c48;
  display: flex;
  flex-direction: column;
  // min-width: 100vw;
  // min-height: 100vh;
}

#titolo {
  padding: 10px;
  display: flex;
  align-items: center;

  h2 {
    margin: 0 15px;
    color: white;
  }
}

.logo {
  height: 50px;
  display: flex;
  align-items: center;
  justify-content: center;

  img {
    width: auto;
    height: 100%;
  }
}

.fascia {
  display: flex;
  align-items: center;
  justify-content: center;
}

.console {
  width: 700px;
  // height: 400px;
  display: flex;
  flex-direction: column;

  select {
    padding: 5px;
    font-size: 11px;
    margin: 15px 5px;
    font-weight: 500;
  }
}

.finestra {
  width: 100%;
  // height: 100%;
  padding: 30px 30px 10px 30px;
  display: flex;
  flex-direction: column;

  background-color: rgb(255, 255, 255);
}

.barra-risultati {
  background-color: #26292d;
  display: flex;
  align-items: center;
  color: white;
  padding: 10px;
  width: 100%;
  height: 38px;
  font-size: 10px;
  font-weight: 600;
}

#lista-personaggi {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
</style>
