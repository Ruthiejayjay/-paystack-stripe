<template>
<div>
  <products-header />
  <products />
</div>
</template>

<script>
import Products from '~/components/products.vue'
import productsHeader from '~/components/productsHeader.vue'
export default {
  components: { productsHeader, Products },
  name: 'IndexPage'
}
</script>
