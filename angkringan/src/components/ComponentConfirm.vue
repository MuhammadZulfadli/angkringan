<template>
  <div>
    <h1>Konfirmasi Transaksi</h1>
    <v-container fluid>
      <!-- <v-card>
        <v-lists class="my-4">
          <v-list-item>
            <h5>ini untuk 2</h5>
            <v-spacer></v-spacer>
            <v-btn>EDIT</v-btn>
            <v-btn success>ACCEPT</v-btn>
            <v-btn danger>CANCEL</v-btn>
          </v-list-item>
        </v-lists>
      </v-card>
      <v-card>
        <v-lists class="my-4">
          <v-list-item>
            <h5>ini untuk 2</h5>
            <v-spacer></v-spacer>
            <v-btn>EDIT</v-btn>
            <v-btn success>ACCEPT</v-btn>
            <v-btn danger>CANCEL</v-btn>
          </v-list-item>
        </v-lists>
      </v-card> -->

      <!-- <v-list>
        <v-list-item>
          <v-list-item-icon>
            <h1>ini untuk coba</h1>
          </v-list-item-icon>
         
          <v-list-item-content>
            <h5>sdfdasfdasff</h5>
          </v-list-item-content>
         
          <v-list-item-action class="baris">
            <v-btn>EDIT</v-btn> ||
            <v-btn color="success">ACCEPT</v-btn>
            <v-btn color="error">CANCEL</v-btn>
          </v-list-item-action>
        </v-list-item>
        <v-list-item>
          <v-list-item-icon>
            <h1>ini untuk coba</h1>
          </v-list-item-icon>
          <v-list-item-content>
            <h5>sdfdasfdasff</h5>
          </v-list-item-content>
          <v-list-item-action class="baris">
            <v-btn>EDIT</v-btn> ||
            <v-btn color="success">ACCEPT</v-btn>
            <v-btn color="error">CANCEL</v-btn>
          </v-list-item-action>
        </v-list-item>
      </v-list> -->

      <v-list v-for="konfirm in koko" :key="konfirm.idKonfirmasi">
        <v-list-group :value="true" prepend-icon="mdi-account-circle">
          <template v-slot:activator>
            <v-list-item-title
              ><h1>#{{ konfirm.idKonfirmasi }}</h1>
            </v-list-item-title>
            <v-btn @click="addItem(konfirm)" color="success">ACC</v-btn>
            <v-btn color="error" @click="hapusItem(konfirm)">Hapus</v-btn>
          </template>
          <v-list-item>
            <template v-slot:default>
              <tbody v-for="menusa in konfirm.menus" :key="menusa.id">
                <tr>
                  <td>{{ menusa.item }}</td>
                  <td>{{ menusa.harga }}</td>
                </tr>
                <tr>
                  <td colspan="2">Total Pesanan</td>
                  <td></td>
                  <td>{{ jml }}</td>
                </tr>
                <tr>
                  <td colspan="4">Harga Total :</td>
                  <td>Rp. {{ parseInt(jumlahTot) }}</td>
                </tr>
              </tbody>
            </template>

            <v-list-item-action class="baris">
              <v-btn>EDIT</v-btn> ||
              <v-btn color="success">ACCEPT</v-btn>
              <v-btn color="error">CANCEL</v-btn>
            </v-list-item-action>
          </v-list-item>
        </v-list-group>
      </v-list>
    </v-container>
    <h1>Report Transaksi</h1>
    <v-list v-for="lapor in laporan" :key="lapor.idKonfirmasi">
      <v-list-item>
        {{ lapor }}
      </v-list-item>
    </v-list>
  </div>
</template>
<script>
import { mapGetters } from "vuex";
export default {
  data() {
    return {
      laporan: [],
      koko: [
        {
          idKonfirmasi: 123,
          menus: [
            {
              item: "kopi",
              harga: 1000
            },
            {
              item: "es teh",
              harga: 30000
            }
          ]
        },
        {
          idKonfirmasi: 231,
          menus: [
            {
              item: "lopa",
              harga: 299
            },
            {
              item: "ioio",
              harga: 30000
            }
          ]
        },
        {
          idKonfirmasi: 1334,
          menus: [
            {
              item: "yuyuy",
              harga: 1000
            },
            {
              item: "es hsdrtgfu",
              harga: 30000
            }
          ]
        },
        {
          idKonfirmasi: 1335,
          menus: [
            {
              item: "yuyuy",
              harga: 1000
            },
            {
              item: "es hsdrtgfu",
              harga: 30000
            }
          ]
        }
      ]
    };
  },
  computed: {
    ...mapGetters(["card"]),
    jumlahTot() {
      return this.koko.reduce((a, b) => a + b.menus.harga, 0);
    },
    cetak() {
      return this.koko;
    }
  },
  mounted() {
    this.koko;
  },
  methods: {
    addItem(item, index) {
      const lopa = this.laporan.push(item);
      if (lopa) {
        this.koko.splice(index, 1);
      }
    },
    hapusItem(index) {
      this.koko.splice(index, 1);
    }
  }
};
</script>
<style>
.baris {
  flex-direction: row;
}
</style>
