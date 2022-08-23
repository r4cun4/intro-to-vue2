<template>
    <div>
      <img
        v-for="(image, index) in imgArr"
        :key="index"
        :src="image.imgSrc"
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
      }
    }
}
</script>

<style>

</style>