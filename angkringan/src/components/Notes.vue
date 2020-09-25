<template>
  <div class="text-center">
    <v-dialog v-model="dialog" width="500">
      <template v-slot:activator="{ on, attrs }">
        <v-btn icon v-bind="attrs" v-on="on">
          <v-icon color="light-blue accent-4">mdi-message-draw</v-icon>
        </v-btn>
      </template>

      <v-card>
        <v-card-title class="headline grey lighten-2"
          >Tambahkan Catatan</v-card-title
        >

        <v-col cols="12" md="6">
          <v-textarea
            name="input-7-1"
            clearable
            label="Catatan Order"
            placeholder="Cth: Ekstra gula, Tidak pakai sambel, & Etc"
            hint="at least max 100 character"
            v-model="ket"
            :maxlength="max"
          ></v-textarea>
        </v-col>
        <v-divider></v-divider>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="primary" text @click="dialog = false">Batal</v-btn>
          <v-btn
            color="primary"
            text
            @click="(dialog = false), addNotesToCard()"
            >Tambah</v-btn
          >
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
export default {
  props: ["id"],
  data() {
    return {
      dialog: false,
      max: 100,
      text: ""
    };
  },
  computed: {
    ...mapGetters(["card"]),
    ket: {
      get() {
        return this.$store.state.ket;
      },
      set(value) {
        this.$store.commit("bindingKet", value);
      }
    }
  },
  methods: {
    addNotesToCard() {
      this.$store.commit("addKeterangan", this.id);
    }
  }
};
</script>

<style>
</style>