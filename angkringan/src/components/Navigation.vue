<template>
  <div>
    <v-container>
      <v-tabs
        centered
        dense
        background-color="transparent"
        color="orange darken-4"
      >
        <v-tab
          class="text-capitalize"
          v-for="link in links"
          :key="link.text"
          :to="link.route"
          >{{ link.text }}
        </v-tab>
      </v-tabs>
    </v-container>
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