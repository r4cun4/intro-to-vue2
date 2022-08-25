<template>
  <div id="app">

    <div class="nav-bar"></div>

    <div class="product-image">
        <ProductImages :imgArr="showImg"/>
    </div>
        
    <div class="product-info">
      <ProductDetails :detailArr="showDetail"/>
      <ProductColors
        :colorArr="showColors"
        @update-product="changeImg($event)" />
    </div>

</div>
<!-- app  -->
</template>

<script>
import ProductImages from './components/ProductImages.vue'
import ProductDetails from './components/ProductDetails.vue'
import ProductColors from './components/ProductColors.vue'

export default {
  name: 'App',
  // activating Vue on the div with the id of app
  components: { ProductImages, ProductDetails, ProductColors },
  data() { 
  //The instance’s data can be accessed from inside the element that the instance is plugged into.
    return {
      selectedVariant: 0,
      inventory: 11,
      cart: 0,
      onSale: true,
      detailArr: ['80% cotton', '20% polyester', 'Gender-neutral'],
      colorArr: ['green', 'blue'],
      image: false,
      imgArr: [
        {
          imgSrc: 'https://www.vuemastery.com/images/challenges/vmSocks-green-onWhite.jpg'
        },
        {
          imgSrc: 'https://www.vuemastery.com/images/challenges/vmSocks-blue-onWhite.jpg'
        }
      ],
      variants: [
        {
          variantId: 2234,
          variantQuantity: 10
        },
        {
          variantId: 2235,
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
    changeImg(index) {
      const greenSocks = document.querySelector('.product-image > div :nth-child(1)')
      const blueSocks = document.querySelector('.product-image > div :nth-child(2)')

      if(index === 0) {
        greenSocks.style.display = 'block'
        blueSocks.style.display = 'none'
      } else {
        greenSocks.style.display = 'none'
        blueSocks.style.display = 'block'
      }
    },
  },
  computed: {
    inStock() {
      return this.variants[this.selectedVariant].variantQuantity
    },
    showDetail() {
      return this.detailArr
    },
    showColors() {
      return this.colorArr
    },
    showImg() {
      return this.imgArr
    }
  },

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
  display: block;
  border: 1px solid #d8d8d8;
  width: 70%;
  margin: 40px;
  box-shadow: 0px .5px 1px #d8d8d8;
  border-radius: 5px;
}

.product-image {
  flex-basis: 40%;
}

.product-info {
  display: flex;
  flex-direction: column;
  align-items: center;
  flex-basis: 60%;
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
