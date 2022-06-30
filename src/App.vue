<template>
  <div>
    <header class="mein">
      <div class="quantity-box">
        <img src="./assets/shopping_cart_PNG38.png" />
        <div class="quantity">{{ cart.length }}</div>
      </div>
      <button v-on:click="navigateTo('products')">View Products</button>
      <br />
      <button v-on:click="navigateTo('cart')">View Cart</button>
    </header>

    <div v-if="page === 'cart'">
      <cart-vew
        v-on:removeItemFromCart="removeItemFromCart"
        :cart="cart"
      ></cart-vew>
    </div>

    <div v-if="page === 'products'">
      <products-vew v-on:addItemToCart="addItemToCart"></products-vew>
    </div>
  </div>
</template>

<script>
import ProductsVew from "./components/ProductsVew.vue";
import CartVew from "./components/CartVew.vue";

export default {
  name: "App",
  data: () => {
    return {
      page: "products",
      cart: [],
    };
  },
  methods: {
    addItemToCart(product) {
      this.cart.push(product);
    },
    removeItemFromCart(product) {
      this.cart.splice(this.cart.indexOf(product));
    },
    navigateTo(page) {
      this.page = page;
    },
  },
  components: {
    ProductsVew,
    CartVew,
  },
};
</script>

<style>
body {
  margin: 0;
}

.products {
  display: grid;
  grid-template-columns: 1fr 1fr;
}

.products button {
  padding: 10px;
  background-color: black;
  color: #ddd;
  outline: none;
  border: none;
  cursor: pointer;
}
</style>

<style scoped>
header {
  padding: 0 2rem;
  height: 60px;
  background-color: rgb(74, 68, 124);
  box-shadow: 2px 2px 5px;
  text-align: right;
  font-size: 30px;
  padding-top: 20px;
}

.quantity-box img {
  height: 50px;
  width: 50px;
  position: relative;
}
.quantity {
  width: 25px;
  height: 25px;
  text-align: center;
  line-height: 25px;
  color: white;
  border-radius: 50%;
  background: red;
  position: absolute;
  top: 9.75px;
  right: 22px;
}

header button {
  padding: 10px;
  border: none;
  cursor: pointer;
  color: white;
  background-color: green;
}
</style>
