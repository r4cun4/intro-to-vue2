<template>
  <div id="app">

    <div class="nav-bar"></div>

    <div class="product-image">
        <ProductImages :imgArr="showImg"/>
    </div>
        
    <div class="product-info">
      <ProductDetails :detailArr="showDetail"/>
      <ProductColors
        :colorArr="stockArr"
        @update-product="changeImg($event)" />
      <ProductStock
        :stockArr="stockArr" 
        :color="currentColor"
       />
    </div>
</div>
<!-- app  -->
</template>

<script>
import ProductImages from './components/ProductImages.vue'
import ProductDetails from './components/ProductDetails.vue'
import ProductColors from './components/ProductColors.vue'
import ProductStock from './components/ProductStock.vue'

export default {
  name: 'App',
  // activating Vue on the div with the id of app
  components: { ProductImages, ProductDetails, ProductColors, ProductStock },
  data() { 
  //The instance’s data can be accessed from inside the element that the instance is plugged into.
    return {
      currentColor : '',
      detailArr: ['80% cotton', '20% polyester', 'Gender-neutral'],
      imgArr: [
        {
          imgSrc: 'https://www.vuemastery.com/images/challenges/vmSocks-green-onWhite.jpg'
        },
        {
          imgSrc: 'https://www.vuemastery.com/images/challenges/vmSocks-blue-onWhite.jpg'
        }
      ],
      stockArr: [
            {
              itemId: 1,
              color: 'green',
              stock: [
                {
                  size : 'S',
                  quantity: 10
                },
                {
                  size : 'M',
                  quantity: 0
                },
                {
                  size: 'L',
                  quantity: 3
                }
              ]
            },
            {
              itemId: 2,
              color: 'blue',
              stock: [
                {
                  size : 'S',
                  quantity: 3
                },
                {
                  size : 'M',
                  quantity: 5
                },
                {
                  size: 'L',
                  quantity: 1
                }
              ]
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
      this.currentColor = this.stockArr[index].color
      const greenSocks = document.querySelector('.product-image > div :nth-child(1)')
      const blueSocks = document.querySelector('.product-image > div :nth-child(2)')

      if(index === 0) {
        greenSocks.style.display = 'block'
        blueSocks.style.display = 'none'
        // document.querySelectorAll('p').style.display = 'block'
        // document.querySelector('p:first-child').style.display = 'block'
        // document.querySelector('p + p').style.display = 'none'
      } else {
        greenSocks.style.display = 'none'
        blueSocks.style.display = 'block'
        // document.querySelectorAll('p').style.display = 'block'
        // document.querySelector('p:first-child').style.display = 'none'
        // document.querySelector('p + p').style.display = 'block'
      }
    },
  },
  computed: {
    // inStock() {
    //   return this.variants[this.selectedVariant].variantQuantity
    // },
    showDetail() {
      return this.detailArr
    },
    showColors() {
      return this.colorArr
    },
    showImg() {
      return this.imgArr
    },
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
  display: block;
  width: 70%;
  margin: 40px;
  border-radius: 5px;
}

.product-image {
  flex-basis: 40%;
  box-shadow: rgb(18 32 53 / 10%) 0px 4px 64px 0px;
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
  border-radius: 10px;
  padding: 10px;
  box-shadow: rgb(18 32 53 / 10%) 0px 4px 64px 0px;
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
