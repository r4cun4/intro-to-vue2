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
            :key="index"
            @click="toggle"
            >
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
        // showStock() {

        //     return this.stockArr.find( obj => obj.color == this.color )?.stock

        // },
        // showStock2() {

        //     const filterElements = this.stockArr.find( obj => obj.color == this.color )
        //     console.log('soy el find', filterElements)

        //     return filterElements ? filterElements.stock : filterElements

        // },
        showStock3() {

            const filterElements = this.stockArr.find( obj => obj.color == this.color )

            if( filterElements ) {
                
                return filterElements.stock
            }

            return this.stockArr[0].stock

        }

    },
    methods: {
        toggle(e) {

            if( e.target.matches('button:first-child') ) {
                document.querySelector('button:first-child + button').classList.remove('active')
                document.querySelector('button:last-child').classList.remove('active')
                e.target.classList.add('active')
            }

            if( e.target.matches('button:first-child + button') ) {
                document.querySelector('button:first-child').classList.remove('active')
                document.querySelector('button:last-child').classList.remove('active')
                e.target.classList.add('active')
            }

            if( e.target.matches('button:last-child') ) {
                document.querySelector('button:first-child').classList.remove('active')
                document.querySelector('button:first-child + button').classList.remove('active')
                e.target.classList.add('active')
            }

        }
    },
    mounted() {
    return this.color[0]
  }
}
</script>

<style scoped>

    div {
        display: flex;
        justify-content: center;
        align-content: center;
        width: 200px;
        padding: 10px;
        box-shadow: rgb(18 32 53 / 10%) 0px 4px 64px 0px;
    }

    button {
        width: 100%;
        margin: 5px;
        padding: 5px;
    }
    .active {
        background: red;
    }

</style>