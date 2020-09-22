<template>
  <div>
    <v-container class="my-5">
      <v-row dense>
        <v-col v-for="mn in minumans" :key="mn.id" cols="12" md="3">
          <v-card>
            <v-img
              :src="mn.src"
              class="white--text align-end"
              gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
              height="200px"
              @click="addItemToCard(mn), (snackbar = true)"
            >
              <v-card-title>{{ mn.item }}</v-card-title>
            </v-img>

            <v-card-actions>
              <v-spacer></v-spacer>

              <v-card-title>Rp. {{ mn.harga }}</v-card-title>
              <!-- Button add -->
              <v-btn @click="addItemToCard(mn), (snackbar = true)" color="primary">Pesan</v-btn>
              <!-- Snackbar Notification -->
              <v-snackbar v-model="snackbar" :timeout="timeout" :top="y === 'top'">
                {{ text }}
                <template v-slot:action="{ attrs }">
                  <v-btn color="red darken-2" text v-bind="attrs" @click="snackbar = false">Close</v-btn>
                </template>
              </v-snackbar>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import { mapActions } from "vuex";
export default {
  name: "Minuman",
  data() {
    return {
      snackbar: false,
      text: "Yeay! Success add to cart",
      timeout: 2000,
      y: "top"
    };
  },
  computed: {
    minumans() {
      return this.$store.getters.getDataM;
    },
    cart() {
      return this.$store.getters.card;
    }
  },
  methods: {
    ...mapActions(["addItemToCard"])
  },
  mounted() {
    console.log(this.cart);
  }
};
</script>

<style></style>
