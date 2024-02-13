<script>
export default {
    name: "Products.vue",
    data() {
        return {
            products: [
                { id: 1, "name": 'Produit A', "quantity": 100, "unit_price": 10, "description": "<b>Description du Produit A</b>" },
                { id: 2, "name": 'Produit B', "quantity": 50, "unit_price": 15, "description": "<b>Description du Produit B</b>" },
                { id: 3, "name": 'Produit C', "quantity": 200, "unit_price": 20, "description": "<b>Description du Produit C</b>" },
                { id: 4, "name": 'Produit D', "quantity": 80, "unit_price": 8, "description": "<b>Description du Produit D</b>" },
                { id: 5, "name": 'Produit E', "quantity": 120, "unit_price": 25, "description": "<b>Description du Produit E</b>" }
            ]
        }
    },
    computed: {
        cheaperProductPrice() {
        if (this.products.length === 0) return 0; // Gérer le cas où il n'y a pas de produits
        return this.products.sort((a, b) => a.unit_price - b.unit_price)[0].unit_price;
        }
    },
    methods: {
    isCheapestProduct(product) {
      // Vérifier si le produit est le moins cher
        const cheapestProduct = this.products.reduce((acc, curr) => acc.unit_price < curr.unit_price ? acc : curr);
        return product === cheapestProduct;
        }
    }
}
</script>

<template>
    <div>
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
            </li>
        </ul>
    </div>
</template>

<style scoped>
.cheapest-product {
    border: 2px solid green;
}
</style>