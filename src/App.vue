<template>
  <div id="app">
    <router-view class="montserrat-font"/>
    <footer-part />
  </div>
</template>

<script>
import FooterPart from './components/Footer.vue';

export default {
  components: {
    FooterPart,
  }
}
</script>

<style>

</style>
