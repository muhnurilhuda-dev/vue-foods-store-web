<template>
  <!-- <h2>{{ product.nama }}</h2> -->
  <div v-if="product.length !== 0">
    <div class="card shadow card-product">
      <img :src="'assets/images/' + product.gambar" class="card-img-top" alt="...">
      <div class="card-body">
        <h5 class="card-title">{{ product.nama }}</h5>
        <p class="card-text">Rp. {{ product.harga }}</p>
        <router-link :to="'/foods/' + product.id" class="btn btn-success">
          <b-icon-cart class="mr-1"></b-icon-cart>
          <strong>Order</strong>
        </router-link>
      </div>
    </div>
  </div>
  <div v-else-if="product.length === 0">
    <div class="d-flex rounded-lg text-center align-self-center justify-content-center" style="color: red; background-color: hotpink;">
      <h2><strong>TIDAK ADA DATA</strong></h2>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardProduct",
  props: ['product']
}
</script>

<style></style>