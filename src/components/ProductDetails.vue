// Challenge:
// Create a new component for product-details with a prop of details.
<template>
    <div>
        <h3>Detalle de producto</h3>
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
}
</script>

<style scoped>

    div {
        border: 1px solid lightgray;
        border-radius: 5px;
        padding: 15px;
        margin: 10px 0 10px;
    }

    ul {
        display: flex;
        justify-content: space-evenly;
        gap: 10px;
        padding: 10px;
    }
    
</style>