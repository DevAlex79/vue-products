<script>

import BillLine from './BillLine.vue';
import Total from './Total.vue';

export default {
    name: 'Bill',
    components: {
        BillLine,
        Total
    },
    data() {
        return {
            lines: []
        };
    },
    methods: {
        addLine() {
            this.lines.push({
                name: '',
                description: '',
                unitPrice: 0,
                quantity: 1
            });
        },
        deleteLine(index) {
            if (this.lines.length > 1) {
                this.lines.splice(index, 1);
            }
        }
    }
};
</script>

<template>
    <div>
        <h1>Facture</h1>
        <button @click="addLine">Ajouter une ligne</button>
        <table>
            <thead>
                <tr>
                    <th>Nom</th>
                    <th>Description</th>
                    <th>Prix unitaire (HT)</th>
                    <th>Quantité</th>
                    <th>Prix total (HT)</th>
                    <th></th>
                </tr>
            </thead>
            <tbody>
                <BillLine v-for="(line, index) in lines" :key="index" :line="line" @delete="deleteLine(index)" />
            </tbody>
        </table>
        <Total :lines="lines" />
    </div>
</template>