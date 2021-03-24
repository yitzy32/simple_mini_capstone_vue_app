<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <!-- <p>{{ products }}</p> -->
    <div v-for="product in products" v-bind:key="product.id">
      {{ product.name }} <br>
      <img v-bind:src="product.image_url">
    </div>
  </div>
</template>
<style>
img {
  width: 250px;
}
</style>
<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome to Vue.js! How do you do",
      products: [],
    };
  },
  created: function () {
    this.indexProducts();
  },
  methods: {
    indexProducts: function () {
      axios.get("http://localhost:3000/api/products").then((response) => {
        console.log(response.data);
        // this.products.data
        this.products = response.data;
      });
    },
  },
};
</script>
