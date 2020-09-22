<template>
  <div class="text-center">
    <v-dialog v-model="dialog" width="500">
      <template v-slot:activator="{ on, attrs }">
        <v-btn icon v-bind="attrs" v-on="on">
          <v-icon color="light-blue accent-4">mdi-message-draw</v-icon>
        </v-btn>
      </template>

      <v-card>
        <v-card-title class="headline grey lighten-2">Tambahkan Catatan</v-card-title>

        <v-col cols="12" md="6">
          <v-textarea
            name="input-7-1"
            label="Catatan Order"
            hint="Cth: Ekstra gula, Tidak pakai sambel, & Etc"
            v-model="keterangan"
          ></v-textarea>
        </v-col>

        <v-divider></v-divider>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="primary" text @click="dialog = false">Batal</v-btn>
          <v-btn color="primary" text @click="dialog = false">Tambah</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
// import { mapActions } from "vuex";
export default {
  data() {
    return {
      dialog: false,
      keterangan: ""
    };
  },
  methods: {
    // ...mapActions(["addNotesToCard"])
    // addNotes() {
    //   this.$store.dispatch("addNotesToCard", this.keterangan);
    // }
  }
};
</script>

<style>
</style>