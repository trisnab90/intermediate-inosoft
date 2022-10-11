<template>
    <div>
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.1/dist/css/bootstrap.min.css" rel="stylesheet">
        <table style="border-spacing: 1rem; text-align: center; width: 50rem;">
            <tr>
                <td>nomer</td>
                <td>Name</td>
                <td>price</td>
                <td>quantity</td>
            </tr>
                <tr v-for="item in allProduct" :key="item.id">
                    <td>{{item.id}}</td>
                    <td>{{item.name}}</td>
                    <td>{{item.price}}</td>
                    <td>{{item.qty}}</td>
                    <td>
                    <button 
                    @click="addToCart(item.id)" style="border-radius: 20px;">Add</button>
                    </td>
                </tr>
    </table>
    </div>
</template>
<script>
export default {
    props: ['allProduct'],
    methods: {
        addToCart(id) {
            this.$emit("emitAddToCart", id);
        },
    }
}
</script>