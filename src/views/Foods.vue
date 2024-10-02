<template>
  <div>
    <navbar />
    <div class="container">
      <div class="row mt-4">
        <div class="col">
          <h2>List of <strong>Foods</strong></h2>
        </div>
      </div>

      <div class="row mt-3">
        <div class="col">
          <div class="input-group mb-3">
            <input 
              v-model="search"
              type="text" 
              class="form-control" 
              placeholder="Find your favorite foods ..." 
              aria-label="Username"
              aria-describedby="basic-addon1"
              @keyup="searchFood"
            >
            <span class="input-group-text" id="basic-addon1">
              <b-icon-search></b-icon-search>
            </span>
          </div>
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
          <div class="d-flex rounded-lg text-center align-items-center justify-content-center w-100"
            style="color: #EF5A6F; background-color: #FF9EAA; height: 120px;">
            <h2><strong>TIDAK ADA DATA</strong></h2>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios"
import Navbar from '@/components/Navbar.vue'
import CardProduct from "@/components/CardProduct.vue";

export default {
  name: "FoodsPage",
  components: {
    Navbar,
    CardProduct
  },
  data() {
    return {
      products: [],
      search: ''
    }
  },
  methods: {
    setProducts(data) {
      this.products = data
    },
    searchFood() {
      axios.get("http://localhost:3000/products?q=" + this.search)
        .then((response) => 
          this.setProducts(response.data)
        )
        .catch((error) => 
          console.log(error)
        )
    }
  },
  mounted() {
    axios.get("http://localhost:3000/products")
      .then((response) => 
        this.setProducts(response.data)
      )
      .catch((error) => 
        console.log(error)
      )
  }
}
</script>