<template>
  <div>
    <v-container>
      <v-card-title class="headline">Transaksi Kamu</v-card-title>
      <v-simple-table fixed-header height="300px">
        <template v-slot:default>
          <thead>
            <tr>
              <th>ID Transaksi</th>
              <th>Tanggal Transaksi</th>
              <th>Nama Item</th>
              <th>Keterangan</th>
              <th>Harga</th>
              <th>Jumlah Pesanan</th>
              <th>Harga Total</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(item, index) in card" :key="item.id">
              <td>{{ index + 1 }}</td>
              <td>{{ tgl }}</td>
              <td>{{ item.item }}</td>
              <td>{{ item.keterangan }}</td>
              <td>{{ item.harga }}</td>
              <td>{{ item.qty }}</td>
              <td>{{ item.qty * item.harga }}</td>
            </tr>
            <tr>
              <td colspan="4">Total Pesanan</td>
              <td></td>
              <td>{{ jml }}</td>
            </tr>
            <tr>
              <td colspan="6">Harga Total :</td>
              <td>{{ jumlahTot }}</td>
            </tr>
          </tbody>
        </template>
      </v-simple-table>
    </v-container>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
export default {
  data() {
    return {};
  },
  computed: {
    ...mapGetters(["card"]),
    jumlahTot() {
      return this.card.reduce((a, b) => a + b.qty * b.harga, 0);
    },
    jml() {
      return this.card.reduce((a, b) => a + b.qty, 0);
    },
    tgl() {
      let date = new Date();
      return date.toDateString();
    }
  },
  mounted() {
    this.card;
  }
};
</script>

<style></style>
