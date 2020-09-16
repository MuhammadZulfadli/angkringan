<template>
  <div>
    <v-card-title>Cart</v-card-title>
    <v-col>
      <v-simple-table :dense="dense" height="300px" :fixed-header="fixedHeader">
        <template v-slot:default>
          <thead>
            <tr>
              <th class="text-left">Gambar</th>
              <th class="text-left">Item</th>
              <th class="text-left">Harga</th>
              <th class="text-left">Jumlah</th>
              <th class="text-left">Total</th>
              <th class="text-left">Action</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="item in items" :key="item.text">
              <td>
                <v-img :src="item.src" class="white--text align-end" height="50px" width="50px"></v-img>
              </td>
              <td>{{item.text}}</td>
              <td>Rp. {{item.price}}</td>
            </tr>
          </tbody>
        </template>
      </v-simple-table>
    </v-col>

    <v-container>
      <v-card-title>Sub Total :</v-card-title>
      <v-card-title>Total :</v-card-title>
      <v-btn class="ma-2" tile color="brown darken-1" dark rounded>Checkout</v-btn>
    </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      fixedHeader: true,
      dense: true,
      item: 1,
      items: [
        {
          text: "Nasi Goreng",
          src:
            "https://images.unsplash.com/photo-1581184953963-d15972933db1?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=574&q=80",
          price: 20000
        }
      ]
    };
  }
};
</script>

<style>
</style>