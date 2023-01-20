<template>
  <div class="home">
    <RemixerProverbios />
  </div>
</template>

<script>
// @ is an alias to /src
import RemixerProverbios from "@/components/RemixerProverbios.vue";

export default {
  name: "HomeView",
  components: {
    RemixerProverbios,
  },
};
</script>
