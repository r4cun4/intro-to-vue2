// Challenge:
// Create a new component for product-details with a prop of details.
<template>
    <div class="product-description">
        <h1>{{ title }}</h1>

        <a :href="link" target="_blank">I am a binded link</a>

        <h3>Product Details</h3>
        <ul>
            <li v-for="(detail, index) in detailArr" :key="index">{{ detail }}</li>
        </ul>
    </div>
</template>

<script>
export default {
    // El nombre de la prop debe ser igual a la data reactiva que se define en la funcion data en su componente padre
    name: 'ProductDetails',
    props: {
            detailArr: {
                type: Array
            }
    },
    data() {
        return {
            product: 'Socks',
            brand: 'Vue Mastery',
            link: 'https://www.vuemastery.com/courses/intro-to-vue-js/attribute-binding'
        }
    },
    computed: {
        title() {
        return this.brand + ' ' + this.product
        },
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
        display: flex;
        justify-content: space-evenly;
        gap: 10px;
        padding: 10px;
    }
    
</style>