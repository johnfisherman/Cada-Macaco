<template>
  <div class="remixer-proverbios">
    <h1>
      Remix de {{ primeirasPartes.length }} Provérbios Populares Portugueses
      (PPP)
    </h1>
    <button
      class="button"
      v-on:click="
        if (index1 > 0) {
          index1--;
        }
      "
    >
      Anterior
    </button>
    <h1>{{ primeirasPartes[index1] }}</h1>
    <button
      class="button"
      v-on:click="
        if (index1 < primeirasPartes.length - 1) {
          index1++;
        }
      "
    >
      Próxima
    </button>

    <br />
    <br />
    <br />
    <button
      class="button"
      v-on:click="
        if (index2 > 0) {
          index2--;
        }
      "
    >
      Anterior
    </button>
    <h1>{{ segundasPartes[index2] }}</h1>
    <button
      class="button"
      v-on:click="
        if (index2 < segundasPartes.length - 1) {
          index2++;
        }
      "
    >
      Próxima
    </button>
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
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
