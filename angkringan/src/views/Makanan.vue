<template>
  <div>
    <v-container class="my-5">
      <v-row dense>
        <v-col
          v-for="makanan in filteredResources()"
          :key="makanan.id"
          cols="12"
          md="3"
        >
          <v-card>
            <v-img
              :src="makanan.src"
              class="white--text align-end"
              gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
              height="200px"
              @click="addItemToCard(makanan), (snackbar = true)"
            >
              <v-card-title>{{ makanan.item }}</v-card-title>
            </v-img>

            <v-card-actions>
              <v-spacer></v-spacer>

              <v-card-title>Rp. {{ makanan.harga }}</v-card-title>
              <v-btn
                @click="addItemToCard(makanan), (snackbar = true)"
                class="mx-6"
                color="primary"
              >
                Pesan
                <!-- <v-icon>mdi-cart</v-icon> -->
              </v-btn>
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
  name: "Makanan",
  components: {},
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

<style></style>
