<template>
  <v-app class="grey lighten-4">
    <!-- <Appbar /> -->
    <v-main>
      <v-container fluid>
        <router-view></router-view>
      </v-container>
    </v-main>
    <!-- <BottomNav /> -->
    <Footer />
  </v-app>
</template>

<script>
// import Appbar from "./components/Appbar";
import Footer from "./views/Footer";
// import BottomNav from "@/components/BottomNav";

export default {
  name: "App",

  components: {
    // Appbar,
    Footer
    // BottomNav
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
