<template>
  <div class="product-cart">
      <div class="container-product--buttons">
        <button 
          @click="addToCart" 
          :disabled="!inStock"
          :class="{ disabledButton: !inStock }"
          >
          +
        </button>
        <button 
          @click="rmvFromCart" 
          >
          -
        </button>
      </div>
      <div class="cart">
        <p>Cart({{ cart }})</p>
      </div>
    </div>
</template>

<script>
export default {

}
</script>

<style>

</style>