<template>
  <v-snackbar v-model="snackbar" :timeout="timeout" :top="y === 'top'">
    {{ text }}
    <template v-slot:action="{ attrs }">
      <v-btn color="red darken-2" text v-bind="attrs" @click="snackbar = false">Close</v-btn>
    </template>
  </v-snackbar>
</template>

<script>
export default {
  data() {
    return {
      snackbar: false,
      text: "Yeay! Success add to cart",
      timeout: 2000,
      y: "top"
    };
  }
};
</script>

<style>
</style>