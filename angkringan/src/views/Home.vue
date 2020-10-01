<template>
  <div>
    <Navigation />
    <!-- minuman -->
    <v-container>
      <v-row>
        <v-col v-for="card in minuman" :key="card.id" cols="12" md="4" sm="6">
          <v-card class="pa-2" outlined shaped>
            <v-img
              :src="card.src"
              class="white--text align-end"
              gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
              height="200px"
              @click="addItemToCard(card), (snackbar = true)"
            >
              <v-card-title class="text">{{ card.item }}</v-card-title>
            </v-img>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-card-title class="text">Rp. {{ card.harga }}</v-card-title>
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
                >
                  Close
                </v-btn>
              </template>
            </v-snackbar>
            <v-btn
              @click="addItemToCard(card), (snackbar = true)"
              class="rounded-br-xl text-capitalize"
              color="white--text orange darken-4"
              width="100%"
              >Pesan</v-btn
            >
          </v-card>
        </v-col>
      </v-row>
    </v-container>
    <!-- Makanan -->
    <v-container class="my-5">
      <v-row>
        <v-col v-for="card in makanan" :key="card.id" cols="12" md="4" sm="6">
          <v-card @click="addItemToCard(card)" class="pa-2" outlined shaped>
            <v-img
              :src="card.src"
              class="white--text align-end"
              gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
              height="200px"
            >
              <v-card-title class="text">{{ card.item }}</v-card-title>
            </v-img>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-card-title class="text">Rp. {{ card.harga }}</v-card-title>
            </v-card-actions>
            <!-- Snackbar -->
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
                >
                  Close
                </v-btn>
              </template>
            </v-snackbar>
            <!-- Order Button -->
            <v-btn
              @click="addItemToCard(card)"
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
  name: "Home",
  data() {
    return {
      snackbar: false,
      text: "Yeay! Success add to cart",
      timeout: 2000,
      y: "top",
    };
  },
  components: {
    Navigation,
  },
  computed: {
    minuman() {
      return this.$store.getters.getDataM;
    },
    makanan() {
      return this.$store.getters.getData;
    },
  },
  methods: {
    ...mapActions(["addItemToCard"]),
  },
};
</script>

<style scoped>
.text {
  font-size: 1.1rem;
  font-weight: 500;
  letter-spacing: -0.015625em;
}
</style>
