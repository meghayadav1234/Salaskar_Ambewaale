<template>
  <v-card>
    <v-toolbar>
      <v-toolbar-title>
        <img :src="getImgUrl()" />
      </v-toolbar-title>

      <v-spacer></v-spacer>
      <v-tabs color="deep-purple accent-4" right>
        <v-tab>Home</v-tab>
        <v-tab>Order Mangoes</v-tab>
        <v-tab>About Us</v-tab>
        <v-tab>Contact Us</v-tab>

        <v-tab-item>
          <Home />
        </v-tab-item>
        <v-tab-item>
          <OrderDetails />
        </v-tab-item>
        <v-tab-item>
          <AboutUs />
        </v-tab-item>
        <v-tab-item>
          <ContactUs />
        </v-tab-item>
      </v-tabs>
    </v-toolbar>
  </v-card>
</template>

<script>
import Home from "./Home";
import AboutUs from "./AboutUs";
import ContactUs from "./ContactUs";
import OrderDetails from "./OrderDetails";

export default {
  name: "NavigationBar",
  components: {
    Home,
    ContactUs,
    AboutUs,
    OrderDetails
  },
  methods: {
    getImgUrl() {
      var images = require.context("../assets/", false, /\.png$/);
      return images("./logo-devgad.png");
    }
  }
};
</script>

<style>
</style>