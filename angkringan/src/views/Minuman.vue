<template>
  <div>
    <Navigation />
    <v-container>
      <v-row>
        <v-col v-for="mn in filteredResources()" :key="mn.id" cols="12" md="3">
          <v-card class="pa-2" outlined shaped>
            <v-img
              :src="mn.src"
              class="white--text align-end"
              gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
              height="200px"
              @click="addItemToCard(mn), (snackbar = true)"
            >
              <v-card-title class="text">{{ mn.item }}</v-card-title>
            </v-img>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-card-title class="text"
                >Rp. {{ mn.harga }}</v-card-title
              > </v-card-actions
            ><!-- Snackbar Notification -->
            <v-snackbar
              v-model="snackbar"
              :timeout="timeout"
              :top="y === 'top'"
            >
              {{ text }}
              <template v-slot:action="{ attrs }">
                <v-btn
                  color="red darken-2"
                  text
                  v-bind="attrs"
                  @click="snackbar = false"
                  >Close</v-btn
                >
              </template>
            </v-snackbar>
            <v-btn
              @click="addItemToCard(mn), (snackbar = true)"
              color="white--text deep-orange"
              class="rounded-br-xl text-capitalize"
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
  name: "Minuman",
  data() {
    return {
      snackbar: false,
      text: "Yeay! Success add to cart",
      timeout: 2000,
      y: "top"
    };
  },
  components: {
    Navigation
  },
  computed: {
    minumans() {
      return this.$store.getters.getDataM;
    },
    cart() {
      return this.$store.getters.card;
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
        return this.minumans.filter(items => {
          return this.searchQuery
            .toLowerCase()
            .split(" ")
            .every(v => items.item.toLowerCase().includes(v));
        });
      } else {
        return this.minumans;
      }
    }
  },
  mounted() {
    console.log(this.cart);
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
