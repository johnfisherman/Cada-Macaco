<template>
  <div class="primeira-parte">
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
  name: "PrimeiraParte",
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
      ],
      segundasPartes: [
        "não movem moinhos.",
        "enche a galinha o papo.",
        "e a caravana passa.",
        "à casa torna.",
        "mais devagar.",
        "desespera.",
        "à casa torna.",
        "no seu galho.",
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
