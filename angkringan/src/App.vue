<template>
  <v-app class="grey lighten-4">
    <Appbar />
    <v-main>
      <Navigation />
      <v-container fluid>
        <router-view></router-view>
      </v-container>
    </v-main>

    <Footer />
  </v-app>
</template>

<script>
import Appbar from "./components/Appbar";
import Footer from "./views/Footer";
import Navigation from "@/components/Navigation";

export default {
  name: "App",

  components: {
    Appbar,
    Footer,
    Navigation
    // Cart
  },

  data: () => ({
    //
  })
};
</script>
<style>
.Grd {
  display: grid;
  grid-template-columns: 2fr 1fr;
}
@media screen and (max-width: 600px) {
  .Grd {
    grid-template-columns: 1fr;
  }
}
</style>
