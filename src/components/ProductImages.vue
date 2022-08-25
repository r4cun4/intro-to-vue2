<template>
    <div>
      <img
        v-for="(image, index) in imgArr"
        :key="index"
        :src="image.imgSrc"
        :alt="altText"
        v-show="index < notFirstProduct"
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
        notFirstProduct: 1
      }
    }
}
</script>

<style scoped>

</style>