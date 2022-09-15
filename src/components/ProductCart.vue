<template>
  <div class="product-cart">
      <div class="container-product--buttons">
        <button 
          @click="$emit('add-event-click')"
          >
          +
        </button>
        <button 
          @click="$emit('sub-event-click')"
          >
          -
        </button>
      </div>
      <div class="cart">
        <p>Cart()</p>
      </div>
    </div>
</template>

<script>
export default {

}
</script>

<style scoped>

  .container-product--buttons {
    display: flex;
    align-items: center;
    justify-content: flex-end;
    width: 100%;
    gap: 15px;
    padding: 10px;
  }

</style>