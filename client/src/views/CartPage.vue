<template>
    <div id="page-wrap">
        <h1>Shopping Cart</h1>
        <hr>
        <CartGrid 
        :products="cartItems" 
        @remove-from-cart="removeFromCart($event)"
        />
        <h3 id="total-price">Total: ${{ totalPrice }}</h3>
        <button id="checkout-button">Proceed to Checkout</button>
    </div>
</template>

<script>
import axios from 'axios';
import CartGrid from '@/components/CartGrid.vue';
export default {
    name: "CartPage",
    components: { CartGrid },
    data() {
        return {
            cartItems: [],
        };
    },
    computed: {
        totalPrice() {
            return this.cartItems.reduce((res, el) => res + Number(el.price), 0);
        }
    },
    methods: {
        async removeFromCart(productId) {
            const response = await axios.delete(`/api/users/123/cart/${productId}`);
            const data = response.data;
            this.cartItems = data
        }
    },
    async created() {
        const response = await axios.get('/api/users/123/cart');
        const res = response.data;
        this.cartItems = res;
    }
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