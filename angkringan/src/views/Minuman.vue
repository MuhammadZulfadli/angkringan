<template>
  <div>
    <Navigation />
    <v-container>
      <v-row>
        <v-col v-for="mn in filteredResources()" :key="mn.id" cols="12" md="3">
          <v-card class="pa-2 rounded-xl card-hover" outlined>
            <v-card-title class="text-item">{{ mn.item }}</v-card-title>
            <v-img
              @click="addItemToCard(mn), notification()"
              :src="mn.src"
              class="white--text align-end rounded-xl"
              gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
              height="180px"
            >
            </v-img>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-card-title class="text-price">Rp. {{ mn.harga }}</v-card-title>
            </v-card-actions>
            <v-btn
              @click="addItemToCard(mn), notification()"
              color="white--text orange darken-4"
              class="rounded-xl text-capitalize"
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
    return {};
  },
  components: {
    Navigation,
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
    },
  },
  methods: {
    ...mapActions(["addItemToCard"]),
    filteredResources() {
      if (this.searchQuery) {
        // console.log(this.searchQuery)
        return this.minumans.filter((items) => {
          return this.searchQuery
            .toLowerCase()
            .split(" ")
            .every((v) => items.item.toLowerCase().includes(v));
        });
      } else {
        return this.minumans;
      }
    },
    notification() {
      return this.$toast.success("Item ditambahkan ke keranjang", {
        position: "top-right",
        type: "success",
        duration: 2000,
        dismissable: true,
      });
    },
  },
  mounted() {
    console.log(this.cart);
  },
};
</script>

<style scoped></style>
