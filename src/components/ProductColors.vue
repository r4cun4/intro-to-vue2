<template>
<div>
  <h3>Available Colors</h3>
    <ul>
      <li v-for="(color, index) in colorArr"
      :key="color"
      class="color-box"
      :style="{ backgroundColor: colorArr[index] }"
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
  }
}
</script>

<style scoped>

div {
        border: 1px solid lightgray;
        border-radius: 5px;
        padding: 15px;
        margin: 40px 0 10px;
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

</style>
