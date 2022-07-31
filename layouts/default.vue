<template>
  <div>
    <products-navbar />
    <Nuxt />
    <products-footer />
  </div>
</template>

<script>
import ProductsFooter from '../components/productsFooter.vue'
import productsNavbar from '../components/productsNavbar.vue'
export default {
  components: { productsNavbar, ProductsFooter },
  head() {
    return {
      title: "payment-gateway-test",
    }
  }
}
</script>

<style>

</style>