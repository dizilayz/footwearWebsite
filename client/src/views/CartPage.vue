<template>
    <div id="page-wrap">
        <h1>Shopping Cart</h1>
        <hr>
        <CartGrid :products="cartItems" />
        <h3 id="total-price">Total: {{ totalPrice }}</h3>
        <button id="checkout-button">Proceed to Checkout</button>
    </div>
</template>

<script>
import CartGrid from '@/components/CartGrid.vue';
import { cartItems } from '@/fakedata';
export default {
    name: "CartPage",
    data() {
        return {
            cartItems
        };
    },
    computed: {
        totalPrice() {
            return this.cartItems.reduce((res, el) => res + Number(el.price), 0);
        }
    },
    components: { CartGrid }
}
</script>

<style scoped>
#checkout-button {
    width: 100%;
}

#total-price {
    padding: 16px;
    text-align: right;
}
</style>