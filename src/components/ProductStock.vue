<template>
    <div>
        <p
          v-for="(item, index) in stockArr"
          :key="index"
          v-show="index === 0">{{ item.itemId }}</p>
    </div>
</template>

<script>
export default {
    name: 'ProductStock',
    props: {
            stockArr: {
                type: Array
            }
    }
}
</script>

<style>

</style>