<template>
  <div>
    <div v-for="it in card" :key="it.id">
      <v-card class="mx-auto" max-width="544" outlined>
        <v-list-item three-line>
          <v-list-item-content>
            <div class="overline mb-4">Cart</div>
            <v-list-item-title class="headline mb-1">{{it.item}}</v-list-item-title>
            <v-list-item-subtitle>Rp. {{it.harga}}</v-list-item-subtitle>
          </v-list-item-content>

          <v-list-item-avatar tile size="80" color="grey">
            <img
              :src="it.src"
              :alt="it.src"
              class="white--text align-end"
              gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
              height="200px"
            />
          </v-list-item-avatar>
        </v-list-item>

        <v-card-actions>
          <v-btn icon>
            <v-icon>mdi-minus-box-outline</v-icon>
          </v-btn>
          <span>0</span>
          <v-btn icon>
            <v-icon>mdi-plus-box</v-icon>
          </v-btn>
          <v-btn icon>
            <v-icon>mdi-trash-can-outline</v-icon>
          </v-btn>
        </v-card-actions>
      </v-card>
    </div>

    <v-card class="mx-auto" max-width="544" outlined>
      <v-card-title>Total :</v-card-title>
      <v-btn class="ma-2" tile color="brown darken-1" dark rounded>Checkout</v-btn>
    </v-card>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
export default {
  data() {
    return {
      // item: 1,
      // items: [
      //   {
      //     text: "Nasi Goreng",
      //     src:
      //       "https://images.unsplash.com/photo-1581184953963-d15972933db1?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=574&q=80",
      //     price: 20000
      //   },
      //   {
      //     text: "Mie Goreng",
      //     src:
      //       "https://images.unsplash.com/photo-1585032226651-759b368d7246?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=597&q=80",
      //     price: 20000
      //   }
      // ]
    };
  },
  computed: {
    ...mapGetters(["card"]),
    jumlah() {
      return this.card.length;
    }
  },
  methods: {}
};
</script>

<style>
</style>