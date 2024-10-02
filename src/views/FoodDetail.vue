<template>
  <div class="food-detail">
    <navbar />
    <div class="container">

      <!-- Breadcrumb -->
      <div class="row mt-5">
        <div class="col">
          <nav aria-label="breadcrumb">
            <ol class="breadcrumb">
              <li class="breadcrumb-item">
                <router-link to="/" class="text-dark">Home</router-link>
              </li>
              <li class="breadcrumb-item">
                <router-link to="/foods" class="text-dark">Foods</router-link>
              </li>
              <li class="breadcrumb-item active" aria-current="page">Food Order</li>
            </ol>
          </nav>
        </div>
      </div>

      <div class="row mt-4">
        <div class="col-md 6">
          <img :src="'../assets/images/' + product.gambar" class="img-fluid shadow" alt="">
        </div>
        <div class="col-md-6">
          <h2><strong>{{ product.nama }}</strong></h2>
          <hr>
          <h4>Harga: <strong>Rp. {{ product.harga }}</strong></h4>
          <form class="mt-4" v-on:submit.prevent>
            <div class="form-group">
              <label for="total_items">Total Items</label>
              <input 
                type="number" 
                class="form-control" 
                v-model="orders.total_items" 
                required
              >
            </div>
            <div class="form-group">
              <label for="detail">Detail</label>
              <textarea 
                v-model="orders.detail"
                class="form-control" 
                placeholder="Detail (ex: spicy, less rice ...)"
              ></textarea>
            </div>

            <button type="submit" class="btn btn-success" @click="makeOrder">
              <b-icon-cart></b-icon-cart>
              Make Order
            </button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Navbar from '@/components/Navbar.vue';

export default {
  name: "FoodDetail",
  components: {
    Navbar
  },
  data() {
    return {
      product: {},
      orders: {},
    }
  },
  mounted() {
    axios.get("http://localhost:3000/products/" + this.$route.params.id)
      .then((response) => 
      this.setProduct(response.data)
    )
    .catch((error) => 
      console.log(error)
    )    
  },
  methods: {
    setProduct(data) {
      this.product = data
    },
    makeOrder() {
      console.log(this.orders);
      this.orders.products = this.product
      axios.post("http://localhost:3000/keranjangs", this.orders)
        .then(() => {
          console.log("Ordering Success")
          // this.$toast.success('Ordered Successfully.', {
          //   type: 'success',
          //   position: 'top-right',
          //   duration: 3000,
          //   dismissible: true
          // })
        })
        .catch((error) => {
          console.log(error)
        })
    }
  }
}
</script>

<style></style>