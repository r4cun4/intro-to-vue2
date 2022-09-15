import { EventBus } from '@/event-bus';
<template>
  <div>
    <!-- two way data binding -->
    <form class="review-form" @submit.prevent="onSubmit">
      
        <p class="error" v-if="errors.length">
          <b>Please correct the following error(s):</b>
          <ul>
            <li v-for="error in errors" :key="error">{{ error }}</li>
          </ul>
        </p>

        <p>
          <label for="name">*Name:</label>
          <input id="name" v-model="name">
        </p>
        
        <p>
          <label for="review">*Review:</label>      
          <textarea id="review" v-model="review"></textarea>
        </p>
        
        <p>
          <label for="rating">*Rating:</label>
          <!-- .number ensures that the data will be converted into an integer -->
          <select id="rating" v-model.number="rating">
            <option>5</option>
            <option>4</option>
            <option>3</option>
            <option>2</option>
            <option>1</option>
          </select>
        </p>

        <div>
            <p>Would you recommend this product? (optional)</p>
            <input type="radio" id="recommendChoice1" name="recommend" value="yes" v-model="recommend">
            <label for="recommendChoice1">yes</label>
            <input type="radio" id="recommendChoice2" name="recommend" value="no" v-model="recommend">
            <label for="recommendChoice2">no</label>
        </div>
            
        <p>
          <input type="submit" value="Submit">  
        </p>    
      
    </form>
  </div>
</template>

<script>
import { eventBus } from '../main'
export default {
    name: 'ProductReview',
    data() {

        return {
            name: null,
            review: null,
            rating: null,
            recommend: null,
            errors: []
        }

    },
    methods: {

        onSubmit() {

            this.errors = []

            if(this.name && this.review && this.rating && this.recommend) {

                let productReview = {
                    name: this.name,
                    review: this.review,
                    rating: this.rating,
                    recommend: this.recommend
                }
                eventBus.$emit('review-submitted', productReview),
                this.name = null
                this.review = null
                this.rating = null
                this.recommend = null

            } else {

                if(!this.name) this.errors.push('Name required.')
                if(!this.review) this.errors.push('Review required')
                if(!this.rating) this.errors.push('Rating required.')

            }
            
        }

    }
}
</script>

<style scoped>
    .review-form {
        box-shadow: rgb(18 32 53 / 10%) 0px 4px 64px 0px;
        padding: 30px;
    }
</style>