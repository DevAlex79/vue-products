<script>
export default {
    name: 'Total',
    props: {
        lines: Array
    },
    computed: {
        totalHT() {
            return this.lines.reduce((acc, line) => acc + (line.unitPrice * line.quantity), 0);
        },
        tva() {
            return this.totalHT * 0.2; // 20% de TVA
        },
        totalTTC() {
            return this.totalHT + this.tva;
        }
    }
};
</script>

<template>
    <div>
        <p>Total HT : {{ totalHT }}</p>
        <p>TVA (20%) : {{ tva }}</p>
        <p>Total TTC : {{ totalTTC }}</p>
    </div>
</template>
