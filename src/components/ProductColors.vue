<template>
<div>
  <h3>Available Colors</h3>
    <ul>
      <li v-for="(item, index) in colorArr"
      :key="index"
      class="color-box"
      :style="{ backgroundColor: item.color }"
      @click="$emit('update-product', index, colorSelected(index))"
      >
      </li>
    </ul>
</div>
  
</template>

<script>
export default {
  name: 'ProductColors',
  props: {
    colorArr: {
      type: Array
    }
  },
  methods: {
    colorSelected(index) {

      // console.log(index)

      if( index === 0 ) {
        document.querySelector('ul > .color-box').style.border = '2px solid black'
        document.querySelector('ul > .color-box + li').style.border = 'none'
      }

       if( index === 1 ) {
        document.querySelector('ul > .color-box + li').style.border = '2px solid black'
        document.querySelector('ul > .color-box').style.border = 'none'
      }
    }
  }
}
</script>

<style scoped>

div {
    border-radius: 5px;
    padding: 15px;
    margin: 40px 0 10px;
    box-shadow: rgb(18 32 53 / 10%) 0px 4px 64px 0px;
    }

ul {
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
}

.color-box {
  width: 40px;
  height: 40px;
  margin: 5px 5px;
  border-radius: 25px;
}

.active {
  border: 2px solid #00bfff;
}

</style>
