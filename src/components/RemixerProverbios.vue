<template>
  <section class="remixer-proverbios">
    <div id="primeiras-partes" class="partes-de-proverbio">
      <button
        class="button"
        :class="{ active: isFirstUpButtonVisible }"
        v-on:click="primeiraNext"
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
        v-on:click="primeiraPrevious"
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
        v-on:click="segundaNext"
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
        v-on:click="segundaPrevious"
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
      <h4>Quem partilha o que tem a mais não é obrigado</h4>
      <p>
        Esta imagem foi gerada com o teu novo provérbio, pronta a ser
        partilhada.👇🏽
      </p>
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
      <a href="https://github.com/johnfisherman/Cada-Macaco" target="_blank"
        >Código aberto</a
      >
      aberto a remixes e novas línguas.
    </p>
    <p>
      Cada Macaco 🙊 permite fazer um total de
      <strong
        >{{
          primeirasPartes.length * primeirasPartes.length
        }}
        combinações</strong
      >
      partir de
      <strong
        >{{ primeirasPartes.length }} Provérbios Populares Portugueses
        (PPP)</strong
      >
      seleccionados a dedo.
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
    <p class="social-links">
      <a class="fr-icon" href="https://fredrocha.net" target="_blank">
        <img src="fr-logo-s.png" alt="Logo for fredrocha.net" />
      </a>
      <a
        class="mastodon-icon"
        href="https://mastodon.social/@john_fisherman"
        target="_blank"
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="40"
          height="40"
          viewBox="0 0 2400 2400"
        >
          <path
            d="M288 128C129 128 0 257 0 416v960c0 159 129 288 288 288h960c159 0 288-129 288-288V416c0-159-129-288-288-288H288zm478.38 219.105h3.45c140.347 1.148 275.434 16.34 354.104 52.473 0 0 156.027 69.805 156.027 307.95 0 0 1.957 175.702-21.76 297.69-15.053 77.44-134.816 162.191-272.367 178.616-71.725 8.558-142.346 16.423-217.65 12.969-123.152-5.642-220.329-29.395-220.329-29.395 0 11.989.739 23.404 2.217 34.08 16.01 121.539 120.515 128.819 219.508 132.213 99.915 3.418 188.88-24.633 188.88-24.633l4.106 90.327s-69.885 37.53-194.382 44.431c-68.65 3.774-153.892-1.726-253.174-28.006-215.325-56.993-252.197-286.524-258.022-519.412-1.728-69.147-.665-134.348-.662-188.88.01-238.144 156.033-307.95 156.033-307.95 78.674-36.133 213.675-51.326 354.022-52.473zM607.544 533.18c-50.528 0-91.234 17.76-122.314 52.408-30.14 34.649-45.145 81.48-45.145 140.412v288.354h114.238V734.476c0-59 24.824-88.944 74.477-88.944 54.9 0 82.42 35.524 82.42 105.766V904.49h113.566V751.3c0-70.242 27.516-105.764 82.414-105.764 49.652 0 74.477 29.945 74.477 88.944v279.876h114.238V726.003c0-58.933-14.473-106.234-45.139-140.412-31.086-34.648-71.792-52.408-122.314-52.408-58.466 0-102.735 22.468-132 67.414L768 648.295l-28.455-47.7c-29.271-44.946-73.542-67.415-132.002-67.415z"
          />
        </svg>
      </a>
      <a
        class="github-icon"
        href="https://github.com/johnfisherman/Cada-Macaco"
        target="_blank"
      >
        <svg viewBox="0 0 1024 1024" xmlns="http://www.w3.org/2000/svg">
          <path
            d="m1024 525c0 225.9-146.6 417.9-348.8 485.8-25.6 5.1-35.2-10.9-35.2-24.4 0-17.2.6-72.3.6-140.8 0-48-16-78.7-34.5-94.7 113.9-12.8 233.6-56.3 233.6-252.8 0-56.3-19.9-101.7-52.5-137.6 5.1-12.8 23-65.3-5.1-135.7 0 0-42.9-14-140.8 52.5-41-11.5-84.5-17.3-128-17.3s-87.1 5.8-128 17.3c-97.9-65.9-140.8-52.5-140.8-52.5-28.2 70.4-10.3 122.9-5.1 135.7-32.7 35.9-52.5 81.9-52.5 137.6 0 195.9 119 240 232.9 252.8-14.7 12.8-28.1 35.2-32.6 68.5-29.4 13.4-103 35.2-149.1-42.2-9.6-15.4-38.4-53.2-78.7-52.5-42.9.6-17.3 24.3.6 33.9 21.8 12.2 46.7 57.6 52.5 72.3 10.2 28.8 43.5 83.9 172.1 60.2 0 42.9.7 83.2.7 95.3 0 13.5-9.6 28.8-35.2 24.4-203.5-67.9-350.1-259.2-350.1-485.8 0-282.9 229.1-512 512-512s512 229.1 512 512z"
            fill="#fff"
            fill-rule="evenodd"
          />
        </svg>
      </a>
    </p>
  </footer>
</template>

<script>
export default {
  name: "RemixerProverbios",
  data() {
    return {
      primeirasPartes: [
        "Cada macaco",
        "Os cães ladram",
        "Grão a grão",
        "Águas passadas",
        "Em terra de cegos",
        "Casa de ferreiro",
        "Água mole em pedra dura",
        "O hábito",
        "Não sirvas a quem serviu",
        "Quanto mais depressa",
        "Quem espera",
        "Há mais marés",
        "Para trás",
        "Quem desdenha",
        "Quem dá e tira",
        "Mais vale andar no mar alto",
        "Casa onde não há pão",
        "Quem vai ao mar",
        "Quem muito dorme",
        "Quem boa cama faz",
        "A árvore caída",
        "Homem prevenido",
        "Longe da vista",
        "Bom filho",
        "Burro gabado",
        "Depressa e bem",
        "Quando a esmola é muita",
        "O que não tem remédio",
        "Quem tem brio",
        "Quem quer bolota",
        "Casa roubada",
        "Roma e Pavia",
        "O barato",
        "Para bom entendedor",
      ],
      segundasPartes: [
        "no seu galho.",
        "e a caravana passa.",
        "enche a galinha o papo.",
        "não movem moinhos.",
        "quem tem um olho é rei.",
        "espeto de pau.",
        "tanto dá até que fura.",
        "não faz o monge.",
        "nem peças a quem pediu.",
        "mais devagar.",
        "desespera.",
        "que marinheiros.",
        "mija a burra.",
        "quer comprar.",
        "para o inferno gira.",
        "do que nas bocas do mundo.",
        "todos ralham ninguém tem razão.",
        "avia-se em terra.",
        "pouco aprende.",
        "nela se deita.",
        "todos vão buscar lenha.",
        "vale por dois.",
        "longe do coração.",
        "à casa torna.",
        "é burro estragado.",
        "há pouco quem.",
        "o pobre desconfia.",
        "remediado está.",
        "não tem frio.",
        "trepa à arvore.",
        "trancas à porta.",
        "não foram feitas num dia.",
        "sai caro",
        "meia palavra basta.",
      ],
      index1: 0,
      index2: 0,
      interactions: 0,
      // After this number of interactions the visitor might need a nudge, some ideas
      suggestionNeeded: 7,
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
    primeiraNext() {
      if (this.index1 < this.primeirasPartes.length - 1) {
        this.index1++;
        this.interactions++;
      }
    },
    primeiraPrevious() {
      if (this.index1 > 0) {
        this.index1--;
        this.interactions++;
      }
    },
    segundaNext() {
      if (this.index2 < this.segundasPartes.length - 1) {
        this.index2++;
        this.interactions++;
      }
    },
    segundaPrevious() {
      if (this.index2 > 0) {
        this.index2--;
        this.interactions++;
      }
    },
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
    this.index1 = this.$route.params.primeira;
    this.index2 = this.$route.params.segunda;
    if (!this.index1) {
      this.index1 = 0;
    }
    if (!this.index2) {
      this.index2 = 0;
    }
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
.partes-de-proverbio button {
  background-color: var(--accent-color);
}
button {
  visibility: hidden;
  background: none;
  border: none;
  /* border: 1px solid #4e4e4e; */
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
  display: none;
}
#sharing-content.active {
  display: block;
}
.sharing-content p {
  font-size: 0.8em;
  margin-bottom: 40px;
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
    padding-right: 2px;
    text-align: right;
  }
  #segundas-partes {
    padding-left: 2px;
    text-align: left;
  }
  .social-sharing img {
    max-width: 500px;
  }
}
@media only screen and (min-width: 1100px) {
  .partes-de-proverbio {
    width: 50%;
  }
  .partes-de-proverbio h3 {
    font-size: 1.5em;
  }
}
@media only screen and (min-width: 1200px) {
  .partes-de-proverbio h3 {
    font-size: 1.6em;
  }
  #primeiras-partes {
    padding-right: 4px;
  }
  #segundas-partes {
    padding-left: 4px;
  }
}
@media only screen and (min-width: 1300px) {
  .partes-de-proverbio h3 {
    font-size: 1.8em;
  }
}
@media only screen and (min-width: 1400px) {
  .partes-de-proverbio h3 {
    font-size: 2em;
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
  color: #554994;
}
footer {
  font-size: 0.7em;
  padding: 20px 40px;
  background-color: var(--tertiary-color);
}
footer a:hover {
  font-style: italic;
}
</style>
