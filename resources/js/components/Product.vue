<template>
    <div style="text-align: left;">
        <h1 class="produk"> All Product</h1>
        <table-all @emitAddToCart="addToCart" :allProduct="allProduct" />
    </div>
</template>
<script>
export default {
    props: ['allProduct'],
    methods: {
        addToCart(id) {
            this.allProduct.forEach((item) => {
                if (item.id === id) {
                    item.qty -= 1
                    item.carts_qty += 1
                } else if (item.qty < 0) {
                    item.qty === 0
                    return false
                } else {
                    return false
                }
                this.$emit("emitAddToCart", id)
            });
        }
    }
}
</script>
<style>
.produk{
    text-align: center;
    border-bottom: groove;
}
</style>