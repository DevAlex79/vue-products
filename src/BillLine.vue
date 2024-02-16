<script>
export default {
    name: 'BillLine',
    props: {
        line: Object
    },
    methods: {
        deleteLine() {
            this.$emit('delete');
        }
    }
};
</script>

<template>
    <tr>
        <td><input v-model="line.name" /></td>
        <td><input v-model="line.description" /></td>
        <td><input type="number" v-model.number="line.unitPrice" /></td>
        <td><input type="number" v-model.number="line.quantity" /></td>
        <td>{{ line.unitPrice * line.quantity }}</td>
        <td><button @click="deleteLine">Supprimer</button></td>
    </tr>
</template>
