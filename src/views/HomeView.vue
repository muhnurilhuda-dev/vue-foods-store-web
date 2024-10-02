<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <navbar />
    <div class="container">
      <hero />

      <div class="row mt-4">
        <div class="col">
          <h2>Best <strong>Foods</strong></h2>
        </div>
        <div class="col">
          <router-link class="btn btn-success float-right" to="/foods">View All
            <b-icon-eye></b-icon-eye>
          </router-link>
        </div>
      </div>


      <div v-if="products.length !== 0">
        <div class="row mb-4">
          <div class="col-md-4 mt-4" v-for="product in products" :key="product.id">
            <card-product :product="product" />
          </div>
        </div>
      </div>
      <div v-else class="col-md-12 mt-4">
        <div class="align-items-center justify-content-center">
          <div
            class="d-flex rounded-lg text-center align-items-center justify-content-center w-100"
            style="color: #EF5A6F; background-color: #FF9EAA; height: 120px;"
          >
            <h2><strong>TIDAK ADA DATA</strong></h2>
          </div>
        </div>
      </div>

    </div>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import axios from 'axios';
import Navbar from '@/components/Navbar.vue'
import Hero from '@/components/Hero.vue';
import CardProduct from '@/components/CardProduct.vue';

export default {
  name: 'HomeView',
  components: {
    // HelloWorld
    Navbar,
    Hero,
    CardProduct
  },
  data() {
    return {
      products: [],
    }
  },
  methods: {
    setProducts(data) {
      this.products = data
    }
  },
  mounted() {
    axios.get("http://localhost:3000/best-products")
      .then((response) =>
        this.setProducts(response.data)
      )
      .catch((error) =>
        console.log(error)
      )
  }
}
</script>
