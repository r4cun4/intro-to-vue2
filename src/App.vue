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

    <div class="container-cart-review">
      <div class="product-cart">
        <ProductCart
          @add-event-click="addToCart"
          @sub-event-click="subFromCart" />
      </div>

      <div class="product-review">
        <ProductTabs
          :reviews="reviews" />
      </div>
    </div>

</div>
<!-- app  -->
</template>

<script>
import { eventBus } from './main'
import ProductImages from './components/ProductImages.vue'
import ProductDetails from './components/ProductDetails.vue'
import ProductColors from './components/ProductColors.vue'
import ProductStock from './components/ProductStock.vue'
import ProductCart from './components/ProductCart.vue'
import ProductTabs from './components/ProductTabs.vue'

export default {

  name: 'App',
  // activating Vue on the div with the id of app
  components: { ProductImages, ProductDetails, ProductColors, ProductStock, ProductCart, ProductTabs },
  data() { 
  //The instance’s data can be accessed from inside the element that the instance is plugged into.
    return {
      currentColor : 'green',
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
      ],
      reviews: []
    }
  },
  methods: {
    addToCart() {
      console.log('soy addToCart')
    },
    subFromCart() {
      console.log('soy subFromCart')
    },
    changeImg(index) {

      this.currentColor = this.stockArr[index].color

      const elFirstImg = document.querySelector('.product-image > div :nth-child(1)')
      const elSecondImg = document.querySelector('.product-image > div :nth-child(2)')

      index === 0 ? elFirstImg.style.display = 'block' : elFirstImg.style.display = 'none'
      index === 1 ? elSecondImg.style.display = 'block' : elSecondImg.style.display = 'none'

    }

  },
  computed: {

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
  mounted() {
    
    const elFirstLi = document.querySelector('ul > .color-box')

    this.currentColor == 'green' ? elFirstLi.classList.add('active') : elFirstLi.classList.remove('active')

    eventBus.$on('review-submitted', productReview => {
      this.reviews.push(productReview)
    })

  }

}
</script>

<style>
#app {
  display: flex;
  flex-wrap: wrap;
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

.container-cart-review {
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: rgb(18 32 53 / 10%) 0px 4px 64px 0px;
  width: 100%;
  margin-top: 50px;
  padding: 25px;
}

.product-cart {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
}

.product-review {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
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

li {
  list-style: none;
}

textarea {
  width: 100%;
  height: 60px;
}

.active {
  border: 3px solid #000;
}

</style>
