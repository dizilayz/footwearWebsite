<template>
    <div>
        <CartGridItem
        v-for="product in products"
        :key="product.id"
        :product="product"
        />
    </div>
</template>

<script>
import CartGridItem from './CartGridItem.vue';

    export default {
    name: "CartGrid",
    props: ["products"],
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