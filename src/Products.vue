<script>

import Product from './Product.vue';

export default {
    name: "Products",
    components: {
        Product
    },
    data() {
        return {
            products: [
                { id: 1, "name": 'Produit A', "quantity": 100, "unit_price": 10, "description": "Description du Produit A", rating: 2.0 },
                { id: 2, "name": 'Produit B', "quantity": 50, "unit_price": 15, "description": "Description du Produit B", rating: 3.8 },
                { id: 3, "name": 'Produit C', "quantity": 200, "unit_price": 20, "description": "Description du Produit C", rating: 4.2 },
                { id: 4, "name": 'Produit D', "quantity": 80, "unit_price": 8, "description": "Description du Produit D", rating: 4.0 },
                { id: 5, "name": 'Produit E', "quantity": 120, "unit_price": 25, "description": "Description du Produit E", rating: 3.7 }
            ]
        }
    },
    computed: {
        cheaperProductPrice() {
            if (this.products.length === 0) return 0; // Gérer le cas où il n'y a pas de produits
            return this.products.reduce((acc, curr) => acc.unit_price < curr.unit_price ? acc : curr).unit_price;
        }
    },
    methods: {
        isCheapestProduct(product) {
            // Vérifier si le produit est le moins cher
            return product.unit_price === this.cheaperProductPrice;
        }
    }
}
</script>

<template>
    <!--<div>
        <h1>Produits</h1>
        <h2>{{ products.length }} produits en vente</h2>
        <p>Prix du produit le moins cher: {{ cheaperProductPrice }}</p>
        <ul>
            <li v-for="(product, index) in products" :key="index" :class="{ 'cheapest-product': isCheapestProduct(product) }">
                <h3>{{ product.name }}</h3>
                <p>ID: {{ product.id }}</p>
                <p>Quantité: {{ product.quantity }}</p>
                <p>Prix unitaire: {{ product.unit_price }}</p>
                <p>Description: {{ product.description }}</p>
                <Product :product="product" :cheaper-product-price="cheaperProductPrice" />
            </li>
        </ul>
    </div>-->
    <div>
        <h1>Produits</h1>
        <h2>{{ products.length }} produits en vente</h2>
        <p>Prix du produit le moins cher: {{ cheaperProductPrice }}</p>
        <ul>
            <Product v-for="(product, index) in products" :key="index" :product="product" :cheaperProductPrice="cheaperProductPrice" />
        </ul>
    </div>
</template>

<style scoped>
.cheapest-product {
    border: 2px solid green;
}
</style>