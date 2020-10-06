<template>
  <div>
    <v-card height="100px">
      <v-bottom-navigation
        fixed
        :value="value"
        absolute
        color="primary"
        horizontal
        cols="12"
      >
        <v-btn>
          <span>Recents</span>

          <v-icon>mdi-history</v-icon>
        </v-btn>

        <v-btn>
          <span>Favorites</span>

          <v-icon>mdi-heart</v-icon>
        </v-btn>

        <v-btn>
          <span>Nearby</span>

          <v-icon>mdi-map-marker</v-icon>
        </v-btn>
      </v-bottom-navigation>
    </v-card>
  </div>
</template>

<script>
export default {
  data() {
    return {
      value: 1
    };
  }
};
</script>

<style>
</style>