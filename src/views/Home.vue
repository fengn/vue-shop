<template>
  <!-- <div class="home"></div> -->
  <!-- <h1 class="text-primary"><fa icon="shopping-cart" />shopping cart</h1> -->

  <section class="container">
    <ranger-selector :products="filteredProducts" v-model="max" />
    <product-list :products="filteredProducts" />
  </section>
</template>

<script>
import ProductList from '@/components/ProductList'
import RangerSelector from '@/components/RangerSelector'

export default {
  name: 'Home',
  data: function() {
    return {
      max: 50,
      cart: []
    }
  },
  props: ['products'],
  components: {
    RangerSelector,
    ProductList
  },
  computed: {
    filteredProducts() {
      return this.products.filter(item => item.price < Number(this.max))
    }
  }
}
</script>
