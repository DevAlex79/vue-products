<script>

import Rating from "./Rating.vue";

export default {
    name: "Product",
    components: {
        Rating
    },
    props: {
        product: {
            type: Object,
            required: true
        },
        cheapestProductPrice: {
            type: Number,
            default: null
        }
    },
    methods: {
        isCheapestProduct() {
            return this.product.unit_price === this.cheapestProductPrice;
        }
    }
}
</script>

<template>
    <div class="product" :class="{ 'cheapest-product': isCheapestProduct }">
        <h3>{{ product.name }}</h3>
        <p>Prix: {{ product.unit_price }}</p>
        <p>Quantité: {{ product.quantity }}</p>
        <p>Description: {{ product.description }}</p>
        <Rating :value="product.rating">
            <template v-slot:default>
        <!-- Mon propre affichage d'étoiles -->
            <span>⭐️⭐️⭐️</span>
            </template>
        </Rating>
    </div>
</template>

<style scoped>
.cheapest-product {
    border: 2px solid green;
}
</style>