<template>
  <div class="home">
    <PrimeiraParte />
  </div>
</template>

<script>
// @ is an alias to /src
import PrimeiraParte from "@/components/PrimeiraParte.vue";

export default {
  name: "HomeView",
  components: {
    PrimeiraParte,
  },
};
</script>
