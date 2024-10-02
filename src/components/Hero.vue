<template>
  <div class="hero">

    <!-- DESKTOP -->
    <div class="d-none d-md-block">
      <div class="row mt-1">
        <div class="col-md-6">
          <div class="d-flex h-100">
            <div class="justify-content-center align-self-center">
              <h2><strong>Delicious Food Menu, </strong><br>in your gadget</h2>
              <p>Let's choose and order your favourite food(s).</p>
              <router-link class="btn btn-lg btn-success" to="/">Order Now
                <b-icon-arrow-right class="ml-1"></b-icon-arrow-right>
              </router-link>
            </div>
          </div>
        </div>
        <div class="col-md-6">
          <img src="../assets/images/hero_bg.png" width="100%" alt="img">
        </div>
      </div>
    </div>

    <!-- MOBILE -->
    <div class="d-sm-block d-md-none">
      <div class="row mt-0">
        <div class="col-md-6 mb-3">
          <img src="../assets/images/hero_bg.png" width="100%" alt="img">
        </div>
        <div class="col-md-6">
          <div class="d-flex h-100">
            <div class="justify-content-center align-self-center">
              <h2><strong>Delicious Food Menu, </strong><br>in your gadget</h2>
              <p>Let's choose and order your favourite food(s).</p>
              <router-link class="btn btn-lg btn-success" to="/">Order Now
                <b-icon-arrow-right class="ml-1"></b-icon-arrow-right>
              </router-link>
            </div>
          </div>
        </div>        
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HeroPage"
}
</script>

<style>

</style>