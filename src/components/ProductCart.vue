<template>
  <div class="product-cart">
      <div class="container-product--buttons">
        <button @click="addToCart">+</button>
        <button @click="subFromCart">-</button>
      </div>
    </div>
</template>

<script>
export default {
  props: {
        stockArr: {
          type: Array
        },
        color: {
          type: String
        }
  },
  methods: {
    addToCart() {
      // this.$emit('add-to-cart')
      const filterElements = this.stockArr.find( obj => obj.color == this.color )
      console.log(filterElements)
    },
    subFromCart() {
      // this.$emit('sub-from-cart')
    }
  }
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