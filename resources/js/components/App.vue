
<template>
    <div class="contain">
        <all-product :allProduct="allProduct" @emitAddToCart="addToCart" />
        <cart :carts="carts" />
    </div>
</template>
    
<script>
export default {
    data() {
        return {
            allProduct: [
                {
                    id: 1,
                    name: "latop",
                    qty: 5,
                    carts_qty: 0,
                    price: 123000,
                    carts_price: 0,
                },
                {
                    id: 2,
                    name: "monitor",
                    qty: 5,
                    carts_qty: 0,
                    price: 2500,
                    carts_price: 0,
                },
                {
                    id: 3,
                    name: "tv",
                    qty: 5,
                    carts_qty: 0,
                    price: 550000,
                    carts_price: 0,
                },
                {
                    id: 4,
                    name: "buku",
                    qty: 5,
                    carts_qty: 0,
                    price: 6600,
                    carts_price: 0,
                },
                {
                    id: 5,
                    name: "pensil",
                    qty: 5,
                    carts_qty: 0,
                    price: 9900,
                    carts_price: 0,
                },
                {
                    id: 6,
                    name: "bulpoint",
                    qty: 5,
                    carts_qty: 0,
                    price: 8900,
                    carts_price: 0,
                },
                {
                    id: 7,
                    name: "mouse",
                    qty: 5,
                    carts_qty: 0,
                    price: 5500,
                    carts_price: 0,
                }
            ],
            carts: []
        }
    },
    methods: {
        addToCart(id) {
            let produk = this.allProduct.find((item) => item.id == id);
            let cart = this.carts.find((item) => item.idProduk == id);
            let idProduk = produk.id;
            let name = produk.name;
            let price = produk.price;
            if (!cart) {
                let cartTotal = {
                    idProduk: idProduk,
                    name: name,
                    price: price,
                    qty: 1,
                    subTotal: price,
                };
                this.carts.push(cartTotal);
                console.log(cartTotal.imgUrl)
            } else {
                cart.qty++;
                cart.subTotal = cart.qty * cart.price;
            }
        },
    }
}
</script>
<style>
button {
    background: rgb(10, 197, 197);
    border: none;
    border-radius: 100%;
    cursor: pointer;
    height: 2rem;
    width: 100%;
}

    .contain {
    margin: 0 auto;
    width: 100%;
    margin-top: 10vh;
    gap: 12rem;
  }

</style>