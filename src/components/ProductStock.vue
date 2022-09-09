<template>
    <div>
        <!-- <button
            v-for="(item, index) in stockArr.find( obj => obj.color == this.color )?.stock"
            :key="index" class="size"
         >
         {{item}}
        </button>   -->

        <button
          v-for="(item, index) in showStock3"
          :key="index">
          {{item.size}} {{item.quantity}}
        </button>
  
    </div>
</template>

<script>

export default {
    name: 'ProductStock',
    props: {
        stockArr: {
            type: Array
        },
        color: {
            type: String
        }
    },
    data() {
        return {
            
        }
    },
    computed: {
        showStock() {

            return this.stockArr.find( obj => obj.color == this.color )?.stock

        },
        showStock2() {

            const filterElements = this.stockArr.find( obj => obj.color == this.color )
            console.log('soy el find', filterElements)

            return filterElements ? filterElements.stock : filterElements

        },
        showStock3() {

            const filterElements = this.stockArr.find( obj => obj.color == this.color )

            if( filterElements ) {
                return filterElements.stock
            }

            return filterElements

        }

    },
}
</script>

<style scoped>

    button {
        width: 100%;
        margin: 5px;
        padding: 5px;
    }

</style>