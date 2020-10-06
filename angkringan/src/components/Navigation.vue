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
    <div>
      <p>Angkringan <strong>4.0</strong></p>
    </div>
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
        <v-text-field
          v-model="message"
          class="mx-3"
          label="Nasi Kucing"
          outlined
          prepend-inner-icon="mdi-magnify"
        ></v-text-field>

        <!-- Cart icon -->
        <v-btn icon class="append button-cart" color="grey" to="/cart">
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
        { icon: "mdi-coffee", text: "Minuman", route: "/minuman" },
        { icon: "mdi-file-chart", text: "Konfirmasi", route: "/konfirmasi" }
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

<style scoped>
.v-btn--icon.v-size--default .v-icon,
.v-btn--fab.v-size--default .v-icon {
  width: 40px;
  height: 40px;
  font-size: 40px;
}

.v-application p {
  font-size: 45px;
  text-align: center;
  color: #1e304d;
}
</style>>
