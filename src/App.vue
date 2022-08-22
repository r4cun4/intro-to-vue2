<template>
  <div id="app">

    <div class="nav-bar"></div>

    <ProductImages :imgArr="showImg"/>

    <div class="product-info">
      <h1>{{ title }}</h1>
      <!-- we are referencing the associated Vue instance’s data, and it replaces that expression with the value of product instead -->
      <a :href="link" target="_blank">Soy un link bindeado</a>

      <span v-if="onSale">{{isOnSale}}</span>
      
      <div class="product-description">
        <ProductDetails :detailArr="showDetail"/>
      </div>

      <div class="product-stock">
        <!-- We can use the v-if and v-else directives to determine which element to render. -->
        <p v-if="inStock"><b>Hay Stock</b></p>
        <p v-else-if="inventory <=10 && inventory > 0">Ultimas unidades!</p>

      <!-- Challenge: -->
      <!-- When inStock is false, bind a class to the “Out of Stock” p tag that adds  text-decoration: line-through to that element. -->
        <p
          v-else
          :style="'color:red'"
          >
          <b>Sin Stock!!!</b>
        </p>

      </div>

      <div class="product-color">
        <h3>Colores disponibles (evento bindeado)</h3>
        <div
          class="color-box"
          v-for="(variant, index) in variants"
          :key="variant.variantId"
          @mouseover="updateProduct(index)"
          :style="{ backgroundColor: variant.variantColor }"
          >
      </div>

      </div>

      <!-- Challenge: -->
      <!-- Add an array of sizes to your data object, then use v-for to display them as a list. -->
      <div class="product-size">
        <h3>Talles disponibles (array de talles)</h3>
        <ul v-for="size in sizes" :key="size.sizeName">
          <li>{{ size.sizeName }}</li>
        </ul>
      </div>

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

    </div>
    <!-- pruduct-info -->

</div>
<!-- app  -->
</template>

<script>
import ProductDetails from './components/ProductDetails.vue'
import ProductImages from './components/ProductImages.vue'

export default {
  name: 'App',
  // activating Vue on the div with the id of app
  components: { ProductImages, ProductDetails },
  data() { 
  //The instance’s data can be accessed from inside the element that the instance is plugged into.
    return {
      product: 'Socks',
      brand: 'Vue Mastery',
      selectedVariant: 0,
      link: 'https://www.vuemastery.com/courses/intro-to-vue-js/attribute-binding',
      inventory: 11,
      cart: 0,
      onSale: true,
      detailArr: ['80% cotton', '20% polyester', 'Gender-neutral'],
      imgArr: ['https://www.vuemastery.com/images/challenges/vmSocks-green-onWhite.jpg', 'https://www.vuemastery.com/images/challenges/vmSocks-blue-onWhite.jpg'],
      variants: [
        {
          variantId: 2234,
          variantColor: 'green',
          variantQuantity: 10
        },
        {
          variantId: 2235,
          variantColor: 'blue',
          variantQuantity: 0
        }
      ],
      sizes: [
        {
          sizeName: 'S'
        },
        {
          sizeName: 'M'
        },
        {
          sizeName: 'L'
        }
      ]
    }
  },
  methods: {
    addToCart() {
      this.cart += 1
    },
    rmvFromCart() {
      if(this.cart > 0) return this.cart -= 1
    },
    updateProduct(index) {
      this.selectedVariant = index
      console.log(index)
    }
  },
  computed: {
    title() {
      return this.brand + ' ' + this.product
    },
    // image() {
    //   return this.variants[this.selectedVariant].variantImage
    // },
    inStock() {
      return this.variants[this.selectedVariant].variantQuantity
    },
    isOnSale() {
      return this.brand + ' ' + this.product + ' En Liquidacion!!!'
    },
    showDetail() {
      return this.detailArr
    },
    showImg() {
      return this.imgArr
    }
  }
}
</script>

<style>
#app {
  display: flex;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
 body {
  font-family: tahoma;
  color: #282828;
  margin: 0px;
}

ul {
  list-style: none;
}

.nav-bar {
  background: linear-gradient(-90deg, #84CF6A, #16C0B0);
  height: 60px;
  margin-bottom: 15px;
}

.product {
  display: flex;
}

img {
  border: 1px solid #d8d8d8;
  width: 70%;
  margin: 40px;
  box-shadow: 0px .5px 1px #d8d8d8;
}

.product-image {
  flex-basis: 700px;
}

.product-info {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-top: 10px;
  flex-basis: 500px;
}

.product-color {
  display: flex;
  flex-wrap: wrap;
}

.product-color h3 {
  width: 100%;
}

.color-box {
  width: 40px;
  height: 40px;
  margin: 5px 5px;
  border-radius: 25px;
}

.product-size {
  display: flex;
  align-items: center;
}

.cart {
  padding: 5px 20px;
}

.product-cart {
  display: flex;
  align-items: center;
  border: 1px solid lightgray;
  border-radius: 10px;
  padding: 10px;
}

.container-product--buttons {
  display: flex;
  flex-direction: column;
  gap: 5px;
}

button {
  border: none;
  background-color: #1E95EA;
  color: white;
  width: 35px;
  font-size: 14px;
} 

.disabledButton {
  background-color: #d8d8d8;
}

.review-form {
  width: 30%;
  padding: 20px;
  border: 1px solid #d8d8d8;  
}

input {
  width: 100%;  
  height: 25px;
  margin-bottom: 20px;
}

li {
  list-style: none;
}

textarea {
  width: 100%;
  height: 60px;
}
</style>
