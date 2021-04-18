<template>
  <div>
    <v-divider></v-divider>
    <v-spacer></v-spacer>
    <v-carousel>
      <v-carousel-item
        v-for="(item,i) in items"
        :key="i"
        :src="getImgUrl(item.src)"
        reverse-transition="fade-transition"
        transition="fade-transition"
      ></v-carousel-item>
    </v-carousel>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      items: [
        {
          src: "mangoHome1"
        },
        {
          src: "mangoHome2"
        },
        {
          src: "mangoHome3"
        }
      ]
    };
  },
  methods: {
    getImgUrl(pet) {
      var images = require.context("../assets/", false, /\.jpg$/);
      return images("./" + pet + ".jpg");
    }
  }
};
</script>

<style>
</style>