<template>
  <div>
    <h1>You Cart</h1>
      <div class="products">
     <div v-for="(product, index) in cart" :key="index">
     {{product.name}}
     <img :src="product.image"/>
     <div>{{product.cost}}</div>
     <button v-on:click="removeItemFromCart(index)">Remove from to Cart</button>
      </div>
     </div>
  </div>
</template>

<script>
export default {
    props: ['cart'],
    methods: {
        removeItemFromCart(index) {
            this.$emit('removeItemFromCart', index)
        }
    }
}
</script>

<style>

</style>