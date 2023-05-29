<template>
    <div>
        <CartGridItem
        v-for="product in cartItems"
        :key="product.id"
        :product="product"
        />
    </div>
</template>

<script>
import CartGridItem from './CartGridItem.vue';

    export default {
    name: "CartGrid",
    props: ["cartItems"],
    components: { CartGridItem }
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