<template>
  <v-app class="grey lighten-4">
    <Appbar />
    <v-main>
      <v-container fluid>
        <div class="Grd">
          <div>
            <router-view></router-view>
          </div>
          <div>
            <Cart />
          </div>
        </div>
      </v-container>
      <!-- <v-container fluid>
      </v-container>
      <router-view></router-view>-->
    </v-main>
    <Footer />
  </v-app>
</template>

<script>
import Appbar from "./components/Appbar";
import Footer from "./views/Footer";
import Cart from "./components/Cart";

export default {
  name: "App",

  components: {
    Appbar,
    Footer,
    Cart
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
</style>
