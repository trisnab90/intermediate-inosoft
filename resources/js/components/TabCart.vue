<template>
    <table style="border-spacing: 1rem; text-align: center; width: 50rem;" v-if="carts.length !== 0">
        <tr>
            <td>Name</td>
            <td>Quantity</td>
            <td>Price</td>
            <td>Action</td>
        </tr>
        <tr v-for="item in carts" :key="item.idProduk">
            <td>{{item.name}}</td>
            <td>{{item.qty}}</td>
            <td>Rp. {{item.subTotal}}</td>
            <td>
                <button @click="subtractCarts(item.idProduk)" style="border-radius: 20px; width: 5rem;">Remove</button>
            </td>
        </tr>
        <tr>
            <td>
                <button @click="checkout" style="border-radius: 20px;">Checkout</button>
            </td>
        </tr>
    </table>
</template>
<script>
export default {
    props: ['carts'],
    data() {
        return {
            total: 0
        }
    },
    methods: {
        subtractCarts(id) {
            this.carts.forEach((cart) => {
                if (cart.idProduk == id) {
                    if (cart.qty === 0) {
                        this.carts.splice(this.carts.indexOf(cart), 1);
                        console.log(cart.subTotal)
                    } else {
                        cart.qty -= 1;
                        cart.subTotal = cart.qty * cart.price;
                    }
                }
            });
        },
        checkout() {
            this.carts.forEach((cart) => {
                this.total += cart.subTotal;
            });
            if (this.carts.length !== 0) {
                alert("Totalnya Adalah Rp." + this.total);
                location.reload();
            } 
        },
    }
}
</script>