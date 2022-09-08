<template>
    <div>
        <p
            v-for="(item, index) in stock"
            :key="index" class="size"
         >
 
        </p>

            <button @click="showSize()">check</button>

    
  
    </div>
</template>

<script>

export default {
    name: 'ProductStock',
    props: {
        stock: {
            type: Array
        },
        color: {
            type: String
        }
    },
    data() {
        return {
            
            isActive : false

        }
    },
    methods: {
        showSize() {

            const filterElements = this.stock.find( obj => obj.color == this.color )
            console.log('soy el find', filterElements)

            filterElements.stock.forEach(items => {

                console.log(items, this.color)

                if(this.color === 'green') {
                    const newP = document.createElement('p')
                    const newContent = document.createTextNode(`${items.size} / ${items.quantity}`)
                    newP.appendChild(newContent)
                    const currentP = document.querySelector('p:first-child')
                    currentP.style.display = 'block'
                    document.querySelector('.size + .size').style.display = 'none'
                    console.log(currentP)
                    currentP.appendChild(newP)
                    this.isActive = true
                }

                if(this.color === 'blue') {
                    const newP = document.createElement('p')
                    const newContent = document.createTextNode(`${items.size} / ${items.quantity}`)
                    newP.appendChild(newContent)
                    const currentP = document.querySelector('.size + .size')
                    currentP.style.display = 'block'
                    document.querySelector('p:first-child').style.display = 'none'
                    currentP.appendChild(newP)
                    this.isActive = true
                }

            });

        }
    }
}
</script>

<style scoped>

    button {
        width: 100%;
        margin: 5px;
        padding: 5px;
    }

</style>