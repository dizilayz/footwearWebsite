<template>
    <div v-if="products.length" >
        <CartGridItem
        v-for="product in products"
        :key="product.id"
        :product="product"
        @remove-from-cart="$emit('remove-from-cart', $event)"
        />
    </div>
    <p v-else>You haven't added anything yet!</p>
</template>

<script>
import CartGridItem from './CartGridItem.vue';

    export default {
    name: "CartGrid",
    props: ["products"],
    components: { CartGridItem },
    methods: {
        removeFromCart() {
            this.$emit('remove-from-cart', this.$event);
        }
    }
}
</script>

<style scoped>
.product-container {
    align-content: 'center';
    border-bottom: 1px solid #ddd;
    display: flex;
    padding: 16px;
    width: 100%;
  }
</style>