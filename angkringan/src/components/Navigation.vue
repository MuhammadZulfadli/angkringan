<template>
  <div>
    <v-tabs fixed-tabs background-color="primary" dark>
      <v-tab v-for="link in links" :key="link.text" :to="link.route"
        >{{ link.text }}
      </v-tab>
    </v-tabs>
  </div>
</template>

<script>
export default {
  data() {
    return {
      links: [
        { text: "All", route: "/" },
        { text: "Makanan", route: "/makanan" },
        { text: "Minuman", route: "/minuman" }
      ]
    };
  }
};
</script>

<style>
</style>