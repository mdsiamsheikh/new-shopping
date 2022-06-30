<template>
    <div>
     <h1>Products</h1>
     <div class="products">
     <div v-for="(product, index) in products" :key="index">
     {{product.name}}
     <img :src="product.image"/>
     <div class="cost">{{product.cost}}</div>
     <button v-on:click="addItemToCart(product)">Add to Cart</button>
      </div>
     </div>
    </div>
</template>

<script>
export default {
   data: () => {
    return {
         products: [
        {
          name: 'Shirt',
          cost: '$10.99',
          image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTAuzwsf4b3NBEpfUh-6muXjy5AoPSuI2tysA&usqp=CAU'
        },
        {
          name: 'Apple iPhone',
          cost: '$100.88',
          image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTVxcKnoAX_D_YSvea85VPt5WO1wsfcE-pbfspK8oU0L1biPRLJeUC0MtS5TJjtWWEN-Jc&usqp=CAU'
        },
      ]
    }
   },
   methods: {
    addItemToCart(product) {
        this.$emit("addItemToCart", product);
    }
   }
}
</script>

<style>
    
</style>