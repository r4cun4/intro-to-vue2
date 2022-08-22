<template>
    <div class="product-image">
      <img
        v-for="(image, index) in images" :key="index"
        :src="imgSrc" 
        :alt="altText"
      />
    </div>
</template>

<script>
export default {
  name: 'ProductImages',
    props: {
            imgArr: {
                type: Array
            }
    },
    data() {
      return {
        altText: 'A pair of socks',
        images: ['https://www.vuemastery.com/images/challenges/vmSocks-green-onWhite.jpg', 'https://www.vuemastery.com/images/challenges/vmSocks-blue-onWhite.jpg'],
      }
    },
    methods: {
      imgSrc() {
        console.log(this.images)
      }
    }

}
</script>

<style>

</style>