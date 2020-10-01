<template>
  <div>
    <v-container class="d-lg-none d-xl-flex">
      <v-btn icon class="pink--text" @click="drawer = true">
        <v-icon>mdi-menu</v-icon>
      </v-btn>
      <v-navigation-drawer v-model="drawer" fixed temporary>
        <v-list nav dense>
          <v-list-item-group active-class="text--accent-4" color="#ED5575">
            <v-list-item
              v-for="link in links"
              :key="link.text"
              :to="link.route"
            >
              <v-list-item-icon>
                <v-icon>{{ link.icon }}</v-icon>
              </v-list-item-icon>
              <v-list-item-title>{{ link.text }}</v-list-item-title>
            </v-list-item>
          </v-list-item-group>
        </v-list>
      </v-navigation-drawer>
    </v-container>
    <v-container class="d-none d-sm-flex d-md-none d-lg-flex">
      <v-tabs
        centered
        cols="12"
        dense
        background-color="transparent"
        color="orange darken-4"
      >
        <v-tab
          class="text-capitalize"
          v-for="link in links"
          :key="link.text"
          :to="link.route"
        >
          {{ link.text }}
        </v-tab>
      </v-tabs>
    </v-container>

    <v-container>
      <div class="d-flex justify-space-between">
        <!-- Search -->
        <div>
          <v-text-field
            v-model="message"
            class="mx-3"
            label="Search"
            outlined
            prepend-inner-icon="mdi-magnify"
            width="200px"
          ></v-text-field>
        </div>

        <!-- Cart icon -->
        <v-btn icon class="append" color="grey" to="/cart">
          <v-icon right>mdi-shopping</v-icon>
          <v-badge color="#ED5575" :content="jumlah"></v-badge>
        </v-btn>
      </div>
    </v-container>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
export default {
  data() {
    return {
      grow: true,
      drawer: false,
      links: [
        { icon: "mdi-home", text: "All", route: "/" },
        { icon: "mdi-food", text: "Makanan", route: "/makanan" },
        { icon: "mdi-coffee", text: "Minuman", route: "/minuman" }
      ]
    };
  },
  computed: {
    ...mapGetters(["card"]),
    jumlah() {
      return this.card.length;
    },
    message: {
      get() {
        return this.$store.getters.searchQuery;
      },
      set(value) {
        this.$store.commit("updateMessage", value);
      }
    }
  }
};
</script>

<style>
</style>