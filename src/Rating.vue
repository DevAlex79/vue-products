<script>
export default {
    name: "Rating",
    props: {
        value: {
            type: Number,
            required: true
        },
        max: {
            type: Number,
            default: 5
        }
    },
    computed: {
        plainStars() {
            return this.value * 100 % 100 === 0 ? this.value : Math.floor(this.value);
        },
        halfStars() {
            return this.value * 100 % 100 !== 0 ? 1 : 0;
        },
        emptyStars() {
            return this.max - Math.floor(this.value);
        }
    }
}
</script>

<template>
    <div class="rating">
    <!-- Utilisation du slot par défaut pour afficher les étoiles -->
        <slot name="default">
            <span v-for="n in plainStars" :key="`star-${n}`">&#9733;</span>
            <span v-if="halfStars">&#9734;</span>
            <span v-for="n in emptyStars" :key="`empty-star-${n}`">&#9734;</span>
        </slot>
    </div>
</template>

<style scoped>
.rating {
  font-size: 24px; /* Taille de la police pour les étoiles */
}

.rating span {
    display: inline-block;
}

.rating span::before {
    content: '\2605'; /* Code Unicode pour une étoile pleine */
    color: #f1c40f; /* Couleur jaune pour les étoiles pleines */
}

.rating span:last-child::before {
    content: '\2605'; /* Code Unicode pour une étoile à moitié pleine */
    color: #f1c40f; /* Couleur jaune pour les étoiles à moitié pleines */
}

.rating span:empty::before {
    content: '\2606'; /* Code Unicode pour une étoile vide */
    color: #ccc; /* Couleur grise pour les étoiles vides */
}
</style>