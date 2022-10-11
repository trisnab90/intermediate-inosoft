<template>
    <div style="text-align: left; width: 50rem;">
        <h1 class="cart">Cart</h1>
        <div>
            <table-cart :carts="carts" />
        </div>
    </div>
</template>
<script>
export default {
    props: ['carts'],
}
</script>
<style>
.cart{
    text-align: center;
    border-bottom: groove;
}
</style>