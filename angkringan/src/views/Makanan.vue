<template>
  <div>
    <Navigation />
    <v-container class="my-5">
      <v-row>
        <v-col
          v-for="makanan in filteredResources()"
          :key="makanan.id"
          cols="12"
          md="3"
        >
          <v-card class="pa-2" outlined shaped>
            <v-img
              :src="makanan.src"
              class="white--text align-end"
              gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
              height="200px"
              @click="addItemToCard(makanan), (snackbar = true)"
            >
              <v-card-title class="text">{{ makanan.item }}</v-card-title>
            </v-img>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-card-title class="text">Rp. {{ makanan.harga }}</v-card-title>
            </v-card-actions>
            <v-snackbar
              v-model="snackbar"
              :timeout="timeout"
              :top="y === 'top'"
            >
              {{ text }}
              <template v-slot:action="{ attrs }">
                <v-btn
                  color="orange darken-4"
                  text
                  v-bind="attrs"
                  @click="snackbar = false"
                  >Close</v-btn
                >
              </template>
            </v-snackbar>
            <v-btn
              @click="addItemToCard(makanan), (snackbar = true)"
              class="rounded-br-xl text-capitalize"
              color="white--text orange darken-4"
              width="100%"
              >Pesan</v-btn
            >
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import Navigation from "@/components/Navigation";
import { mapActions } from "vuex";
export default {
  name: "Makanan",
  components: {
    Navigation
  },
  data() {
    return {
      snackbar: false,
      text: "Yeay! Success add to cart",
      timeout: 2000,
      y: "top"
    };
  },
  computed: {
    makanans() {
      return this.$store.getters.getData;
    },
    searchQuery() {
      return this.$store.getters.searchQuery;
    }
  },
  methods: {
    ...mapActions(["addItemToCard"]),
    filteredResources() {
      if (this.searchQuery) {
        // console.log(this.searchQuery)
        return this.makanans.filter(items => {
          return this.searchQuery
            .toLowerCase()
            .split(" ")
            .every(v => items.item.toLowerCase().includes(v));
        });
      } else {
        return this.makanans;
      }
    }
  }
};
</script>

<style scoped>
.text {
  font-size: 1.1rem;
  font-weight: 500;
  letter-spacing: -0.015625em;
}
</style>