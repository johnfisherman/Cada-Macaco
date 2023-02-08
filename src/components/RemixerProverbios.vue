<template>
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
  <section class="social-sharing">
    <button
      id="sharing-button"
      :class="{
        pressed: isSharingContentActive,
        active: isSharingButtonButtonActive,
      }"
      v-on:click="isSharingContentActive = true"
    >
      💡 Já sei quem vai gostar disto!
    </button>
    <button
      id="proverbios-shuffle-button"
      :class="{ active: isShuffleButtonActive }"
      v-on:click="shuffleProverbios()"
    >
      🎲 Dá-me um provérbio à sorte!
    </button>
    <div :class="{ active: isSharingContentActive }" id="sharing-content">
      <h4>Quem partilha o que tem a mais não é obrigado 👇🏽</h4>
      <img :src="generated()" v-if="poster" class="md:max-w-md" />
      <p>Botão direito > Gravar como (ou "Download")</p>
    </div>
  </section>
  <footer>
    <p>
      Uma experiência linguística de
      <a href="https://fredrocha.net">Fred Rocha</a> com a inspiração de
      <a href="https://madalenamarques.com" target="_blank">Madalena Marques</a
      >.
      <a
        href="https://github.com/johnfisherman/os-caes-ladram-no-seu-galho"
        target="_blank"
        >Código aberto</a
      >
      aberto a remixes e novas línguas.
    </p>
    <p>
      Cães ladram permite fazer um total
      {{ primeirasPartes.length * primeirasPartes.length }} de combinações a
      partir de {{ primeirasPartes.length }} Provérbios Populares Portugueses
      (PPP) seleccionados a dedo.
    </p>
    <p>
      Logo e ícone por
      <a
        href="https://www.flaticon.com/authors/freepik"
        title="muted monkey"
        target="_blank"
        >Freepik</a
      >.
    </p>
  </footer>
</template>

<script>
export default {
  name: "RemixerProverbios",
  data() {
    return {
      primeirasPartes: [
        "Casa onde não há pão",
        "Mais vale andar no mar alto",
        "Cada macaco",
        "Águas passadas",
        "Grão a grão",
        "Os cães ladram",
        "O hábito",
        "Bom filho",
        "Quanto mais depressa",
        "Quem espera",
        "Quando a esmola é muita",
        "Há mais marés",
        "Quem dá e tira",
        "Em terra de cegos",
        "Casa de ferreiro",
        "Quem vai ao mar",
        "Quem muito dorme",
        "Quem boa cama faz",
        "A árvore caída",
        "Homem prevenido",
        "Quem desdenha",
        "Longe da vista",
        "Para trás",
        "Burro gabado",
        "Depressa e bem",
        "O que não tem remédio",
        "Água mole em pedra dura",
        "Quem tem brio",
        "Quem quer bolota",
        "Casa roubada",
        "Não sirvas a quem serviu",
        "Roma e Pavia",
      ],
      segundasPartes: [
        "todos ralham ninguém tem razão.",
        "do que nas bocas do mundo.",
        "no seu galho.",
        "não movem moinhos.",
        "enche a galinha o papo.",
        "e a caravana passa.",
        "não faz o monge.",
        "à casa torna.",
        "mais devagar.",
        "desespera.",
        "o pobre desconfia.",
        "que marinheiros.",
        "para o inferno gira.",
        "quem tem um olho é rei.",
        "espeto de pau.",
        "avia-se em terra.",
        "pouco aprende.",
        "nela se deita.",
        "todos vão buscar lenha.",
        "vale por dois.",
        "quer comprar.",
        "longe do coração.",
        "mija a burra.",
        "é burro estragado.",
        "há pouco quem.",
        "remediado está.",
        "tanto dá até que fura.",
        "não tem frio.",
        "trepa à arvore.",
        "trancas à porta.",
        "nem peças a quem pediu.",
        "não foram feitas num dia.",
      ],
      index1: 0,
      index2: 0,
      interactions: 0,
      // After this number of interactions the visitor might need a nudge, some ideas
      suggestionNeeded: 2,
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
    isShuffleButtonActive() {
      return this.interactions > this.suggestionNeeded;
    },
    isSharingButtonButtonActive() {
      return this.interactions > 0;
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
        let font = new FontFace("Castoro", `url(fonts/Castoro-Regular.ttf)`);
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
      let canvas = document.createElement("canvas");
      canvas.width = 1332;
      canvas.height = 888;
      let context = canvas.getContext("2d");
      let poster = this.poster;
      // console.log(poster instanceof HTMLImageElement);

      context.drawImage(poster, 0, 0);
      context.font = "56px Castoro";
      context.textAlign = "center";
      context.textBaseline = "top";
      context.fillText(
        this.primeirasPartes[this.index1] +
          " " +
          this.segundasPartes[this.index2],
        650,
        380
      );
      context.font = "36px Castoro";
      context.fillText("criado em https://cadamaca.co", 650, 800);
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
h3 {
  font-weight: 300;
}
.remixer-proverbios {
  /* border: 1px solid hotpink !important; */
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 80px 0 0 0;
  margin-bottom: 40px;
  font-size: 22px;
  color: var(--main-font-color);
}
.partes-de-proverbio {
  font-size: 1em;
  font-family: var(--serifed-font-family);
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
button.active:hover {
  transform: scale(1.1);
  cursor: pointer;
  transition: all ease-in-out 0.1s;
}
button:active {
  background-color: var(--active-button-bg-color);
}
button#proverbios-shuffle-button {
  width: 300px;
  padding-top: 10px;
  padding-bottom: 10px;
  font-size: 0.7em;
  margin-bottom: 20px;
  visibility: visible;
  border: 1px solid #c6c6c6;
  color: #c6c6c6;
  opacity: 0.5;
}
button#proverbios-shuffle-button.active {
  border: 1px solid #4e4e4e;
  color: var(--main-font-color);
  opacity: 1;
}
button#sharing-button {
  width: 300px;
  padding-top: 10px;
  padding-bottom: 10px;
  font-size: 0.7em;
  visibility: visible;
  border: 1px solid #c6c6c6;
  color: #c6c6c6;
}
button#sharing-button.active {
  border: 1px solid #4e4e4e;
  color: var(--main-font-color);
  opacity: 1;
}
.social-sharing {
  padding-bottom: 120px;
}
button#sharing-button {
  margin-bottom: 20px;
}
button#sharing-button.pressed {
  background-color: #2c3e50;
  color: white;
  cursor: default;
}
button#sharing-button.pressed:hover {
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
  .remixer-proverbios {
    flex-direction: row;
  }
  .partes-de-proverbio {
    width: 40%;
  }
  .partes-de-proverbio h3 {
    font-size: 1em;
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
@media only screen and (min-width: 1100px) {
  .partes-de-proverbio h3 {
    font-size: 1.4em;
    /* border: 1px solid teal !important; */
  }
}
@media only screen and (min-width: 1200px) {
  .partes-de-proverbio h3 {
    font-size: 1.5em;
    /* border: 1px solid lightcoral !important; */
  }
}
@media only screen and (min-width: 1300px) {
  .partes-de-proverbio h3 {
    font-size: 1.6em;
    /* border: 1px solid hotpink !important; */
  }
}
@media only screen and (min-width: 1400px) {
  .partes-de-proverbio h3 {
    font-size: 1.7em;
    /* border: 1px solid greenyellow !important; */
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
footer {
  font-size: 1em;
  color: lightslategray;
}
</style>
