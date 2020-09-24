<template>
  <div>
    <v-tabs dense fixed-tabs background-color="transparent" color="primary">
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
      grow: true,
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