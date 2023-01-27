<template>
  <h5>{{ primeirasPartes.length }} Provérbios Populares Portugueses (PPP)</h5>
  <section class="remixer-proverbios">
    <div id="primeiras-partes" class="partes-de-proverbio">
      <button
        class="button"
        :class="{ active: isFirstUpButtonVisible }"
        v-on:click="
          if (index1 < primeirasPartes.length - 1) {
            index1++;
            interactions++;
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
            interactions++;
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
            interactions++;
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
            interactions++;
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
  </section>
  <div class="proverbios-shuffle" v-show="interactions > suggestionNeeded">
    <button
      id="proverbios-shuffle-button"
      class="active"
      v-on:click="shuffleProverbios()"
    >
      Dá aí uma ideia!
    </button>
  </div>
  <section class="social-sharing">
    <button
      id="sharing-button"
      class="active"
      :class="{ pressed: isSharingContentActive }"
      v-on:click="isSharingContentActive = true"
    >
      Já sei quem vai gostar disto!
    </button>
    <div :class="{ active: isSharingContentActive }" id="sharing-content">
      <img :src="generated()" v-if="poster" class="md:max-w-md" />
      <p>Botão direito > Gravar como (ou Download)</p>
    </div>
  </section>
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
        "O hábito",
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
        "Para trás",
        "Burro gabado",
        "Depressa e bem",
        "O que não tem remédio",
      ],
      segundasPartes: [
        "não movem moinhos.",
        "enche a galinha o papo.",
        "e a caravana passa.",
        "não faz o monge.",
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
        "todos vão buscar lenha.",
        "vale por dois.",
        "quer comprar.",
        "longe do coração.",
        "mija a burra.",
        "é burro estragado.",
        "há pouco quem.",
        "remediado está.",
      ],
      index1: 0,
      index2: 0,
      interactions: 0,
      // After this number of interactions the visitor might need a nudge, some ideas
      suggestionNeeded: 10,
      poster: null,
      isSharingContentActive: false,
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
  methods: {
    shuffleProverbios() {
      this.index1 = Math.floor(Math.random() * this.primeirasPartes.length);
      this.index2 = Math.floor(Math.random() * this.segundasPartes.length);
      return true;
    },
    loadImage(url) {
      return new Promise((resolve) => {
        // console.log("Loading image...");
        let img = new Image();
        img.onload = () => {
          resolve(img);
        };
        img.crossOrigin = "Anonymous";
        img.src = url;
      });
    },
    loadFont() {
      return new Promise((resolve) => {
        let font = new FontFace(
          "SF Movie Poster",
          `url(https://assets.codepen.io/141041/sf-movie-poster-webfont.woff)`
        );
        font
          .load()
          .then((face) => {
            document.fonts.add(face);
            resolve();
          })
          .catch();
      });
    },
    generated() {
      // console.log("Generating image...");

      let canvas = document.createElement("canvas");
      canvas.width = 1332;
      canvas.height = 888;
      let context = canvas.getContext("2d");
      let ppp = this.poster;
      // console.log(ppp instanceof HTMLImageElement);

      context.drawImage(ppp, 0, 0);
      context.font = "96px SF Movie Poster";
      context.textAlign = "center";
      context.textBaseline = "top";
      context.fillText(
        this.primeirasPartes[this.index1] +
          " " +
          this.segundasPartes[this.index2],
        650,
        380
      );
      return canvas.toDataURL("image/jpeg");
    },
  },
  async created() {
    // console.log("The component is now created.");
    await this.loadFont();
    this.poster = await this.loadImage("card-for-sharing.jpg");
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
  margin-bottom: 40px;
}
#primeiras-partes {
  /* border: 1px solid black !important; */
}
#segundas-partes {
  /* border: 1px solid palegreen !important; */
}
button {
  visibility: hidden;
  background: none;
  border: none;
  border: 1px solid #4e4e4e;
  width: 60px;
  margin: 0px 40px;
  border-radius: 4px;
}
button.active {
  visibility: visible;
}
button:hover {
  transform: scale(1.1);
  cursor: pointer;
  transition: all ease-in-out 0.1s;
}
button:active {
  background-color: #dedede;
}
button#proverbios-shuffle-button {
  width: 200px;
  padding-top: 10px;
  padding-bottom: 10px;
}
button#sharing-button {
  width: 200px;
  padding-top: 10px;
  padding-bottom: 10px;
}
.social-sharing {
  padding-bottom: 120px;
}
.social-sharing button {
  margin-bottom: 40px;
}
.social-sharing button.pressed {
  background-color: #2c3e50;
  color: white;
}
.social-sharing button.pressed:hover {
  transform: scale(1);
}
.social-sharing img {
  max-width: 100%;
}
#sharing-content {
  visibility: hidden;
}
#sharing-content.active {
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
    padding-right: 5px;
    text-align: right;
  }
  #segundas-partes {
    /* border: 1px solid palegreen !important; */
    padding-left: 5px;
    text-align: left;
  }
  .social-sharing img {
    max-width: 500px;
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
