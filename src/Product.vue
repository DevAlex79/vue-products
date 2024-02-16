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
            required: true  //default: null
        }
    },
    computed: {
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
            <!-- Affichage des étoiles pleines -->
            <template v-slot:plain>
                <span class="plain-star">&#9733;</span>
            </template>
            <!-- Affichage des étoiles à moitié pleines -->
            <template v-slot:half>
                <span class="half-star">&#9733;</span>
            </template>
            <!-- Affichage des étoiles vides -->
            <template v-slot:empty>
                <span class="empty-star">&#9734;</span>
            </template>
        </Rating>
    </div>
</template>


<style scoped>
.cheapest-product {
    border: 2px solid green;
}
</style>