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
        <slot name="plain">
            <span class="plain-star">&#9733;</span>
        </slot>
        <slot name="half">
            <span class="half-star">&#9734;</span>
        </slot>
        <slot name="empty">
            <span class="empty-star">&#9734;</span>
        </slot>
    </div>
</template>


<style scoped>
.rating {
  font-size: 24px; /* Taille de la police pour les étoiles */
}

.plain-star {
  color: #f1c40f; /* Couleur jaune pour les étoiles pleines */
}

.half-star {
  color: #f1c40f; /* Couleur jaune pour les étoiles à moitié pleines */
}

.empty-star {
  color: #ccc; /* Couleur grise pour les étoiles vides */
}
</style>