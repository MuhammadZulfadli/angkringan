<template>
  <div>
    <v-container>
      <v-card-title class="headline">Transaksi Kamu</v-card-title>
      <v-simple-table fixed-header height="600px">
        <template v-slot:default>
          <thead>
            <tr>
              <td>ID Transaksi : #{{ idPesan }}</td>
              <td>Tanggal Transaksi : {{ tgl }}</td>
            </tr>
            <tr>
              <th>Nama Item</th>
              <th>Keterangan</th>
              <th>Harga</th>
              <th>Jumlah Pesanan</th>
              <th>Harga Total</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="item in card" :key="item.id">
              <td>{{ item.item }}</td>
              <td>{{ item.keterangan }}</td>
              <td>Rp. {{ item.harga }}</td>
              <td>{{ item.qty }}</td>
              <td>Rp. {{ item.qty * item.harga }}</td>
            </tr>
            <tr>
              <td colspan="2">Total Pesanan</td>
              <td></td>
              <td>{{ jml }}</td>
            </tr>
            <tr>
              <td colspan="4">Harga Total :</td>
              <td>Rp. {{ jumlahTot }}</td>
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
    },
    idPesan() {
      // return Math.floor(Math.random() * 300);
      let a = 0;
      a += `00` + 1;
      return a;
    }
  },
  mounted() {
    this.card;
  }
};
</script>

<style></style>
