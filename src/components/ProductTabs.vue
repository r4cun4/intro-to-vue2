<template>

    <div>
        <span class="tab"
        :class="{activateTab: selectedTab === tab}"
        v-for="(tab, index) in tabs"
        :key="index"
        @click="selectedTab = tab"
        >
        {{tab}}</span>

        <div class="product-review" v-show="selectedTab === 'Reviews'">
            <p v-if="!reviews.length">There are no reviews yet.</p>
            <ul v-else>
                <li v-for="(review, index) in reviews" :key="index">
                    <p>{{ review.name }}</p>
                    <p>Rating:{{ review.rating }}</p>
                    <p>{{ review.review }}</p>
                </li>
            </ul>
        </div>

        <div v-show="selectedTab === 'Make a Review'">
             <ProductReview />
        </div>

    </div>
    
</template>

<script>
import ProductReview from './ProductReview.vue'
export default {
    name: 'ProductTabs',
    components: {ProductReview},
    props: {
        reviews: {
            type: Array,
            required: true
        }
    },
    data() {
        return {
            tabs: ['Reviews', 'Make a Review'],
            selectedTab: 'Reviews'
        }
    }
}
</script>

<style scoped>

.tab {
    cursor: pointer;
}

.tab.activateTab {
    color: #16C0B0;
    text-decoration: underline;
}

</style>