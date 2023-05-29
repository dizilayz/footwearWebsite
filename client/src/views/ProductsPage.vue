<template>
    <div id="page-wrap">
        <ProductsGrid 
        :products="products"
        />
    </div>
</template>

<script>
import ProductsGrid from '@/components/ProductsGrid.vue';
import { products } from '@/fakedata';

export default {
    name: "ProductsPage",
    components: { ProductsGrid },
    data() {
        return {
            products,
        };
    },
}
</script>
