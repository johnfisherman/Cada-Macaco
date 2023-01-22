<template>
  <h1>
    Remix de {{ primeirasPartes.length }} Provérbios Populares Portugueses (PPP)
  </h1>
  <div class="remixer-proverbios">
    <div id="primeiras-partes" class="partes-de-proverbio">
      <button
        class="button"
        :class="{ active: isFirstUpButtonVisible }"
        v-on:click="
          if (index1 < primeirasPartes.length - 1) {
            index1++;
          }
        "
      >
        <svg
          fill="none"
          height="24"
          viewBox="0 0 24 24"
          width="24"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="m4 16 8-8 8 8"
            stroke="#000"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
          />
        </svg>
      </button>
      <h3>{{ primeirasPartes[index1] }}</h3>
      <button
        class="button"
        :class="{ active: isFirstDownButtonVisible }"
        v-on:click="
          if (index1 > 0) {
            index1--;
          }
        "
      >
        <svg
          fill="none"
          height="24"
          viewBox="0 0 24 24"
          width="24"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="m4 8 8 8 8-8"
            stroke="#000"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
          />
        </svg>
      </button>
    </div>
    <div id="segundas-partes" class="partes-de-proverbio">
      <button
        class="button"
        :class="{ active: isSecondUpButtonVisible }"
        v-on:click="
          if (index2 < segundasPartes.length - 1) {
            index2++;
          }
        "
      >
        <svg
          fill="none"
          height="24"
          viewBox="0 0 24 24"
          width="24"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="m4 16 8-8 8 8"
            stroke="#000"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
          />
        </svg>
      </button>
      <h3>{{ segundasPartes[index2] }}</h3>
      <button
        class="button"
        :class="{ active: isSecondDownButtonVisible }"
        v-on:click="
          if (index2 > 0) {
            index2--;
          }
        "
      >
        <svg
          fill="none"
          height="24"
          viewBox="0 0 24 24"
          width="24"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="m4 8 8 8 8-8"
            stroke="#000"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
          />
        </svg>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "RemixerProverbios",
  data() {
    return {
      primeirasPartes: [
        "Águas passadas",
        "Grão a grão",
        "Os cães ladram",
        "Bom filho",
        "Quanto mais depressa",
        "Quem espera",
        "Quando a esmola é muita",
        "Cada macaco",
        "Há mais marés",
        "Quem dá e tira",
        "Em terra de cegos",
        "Casa de ferreiro",
        "Quem vai ao mar",
        "Quem muito dorme",
        "Mais vale andar no mar alto",
        "Quem boa cama faz",
        "A árvore caída",
        "Homem prevenido",
        "Quem desdenha",
        "Longe da vista",
      ],
      segundasPartes: [
        "não movem moinhos.",
        "enche a galinha o papo.",
        "e a caravana passa.",
        "à casa torna.",
        "mais devagar.",
        "desespera.",
        "o pobre desconfia.",
        "no seu galho.",
        "que marinheiros.",
        "para o inferno gira.",
        "quem tem um olho é rei.",
        "espeto de pau.",
        "avia-se em terra.",
        "pouco aprende.",
        "do que nas bocas do mundo.",
        "nela se deita.",
        "vale por dois.",
        "longe do coração.",
      ],
      index1: 0,
      index2: 0,
    };
  },
  props: {
    msg: String,
  },
  computed: {
    isFirstUpButtonVisible() {
      return this.index1 < this.primeirasPartes.length - 1;
    },
    isFirstDownButtonVisible() {
      return this.index1 > 0;
    },
    isSecondUpButtonVisible() {
      return this.index2 < this.segundasPartes.length - 1;
    },
    isSecondDownButtonVisible() {
      return this.index2 > 0;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  margin: 20px 0 80px 0;
}
.remixer-proverbios {
  /* border: 1px solid hotpink !important; */
  display: flex;
  flex-direction: column;
  justify-content: center;
}
#primeiras-partes {
  /* border: 1px solid black !important; */
}
#segundas-partes {
  /* border: 1px solid palegreen !important; */
}
button {
  visibility: hidden;
}
button.active {
  visibility: visible;
}
@media only screen and (min-width: 800px) {
  h3 {
    font-size: 1.5em;
  }
  .remixer-proverbios {
    flex-direction: row;
  }
  .partes-de-proverbio {
    width: 40%;
  }
  #primeiras-partes {
    /* border: 1px solid black !important; */
    padding-right: 10px;
    text-align: right;
  }
  #segundas-partes {
    /* border: 1px solid palegreen !important; */
    padding-left: 10px;
    text-align: left;
  }
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
