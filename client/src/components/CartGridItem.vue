<template>
    <div class="product-container">
            <img class="product-image" :src="product.imageUrl">
            <div class="details-wrap">
              <h3>{{ product.name }}</h3>
              <p>${{ product.price }}</p>
            </div>
            <button
            @click="$emit('remove-from-cart', product.id)"
            class="remove-button"
            >Remove</button>
    </div>
</template>

<script>
    export default {
        name: 'CardGridItem',
        props: ['product'],
    }
</script>

<style scoped>
h1 {
  border-bottom: 1px solid black;
  margin: 0;
  margin-top: 16px;
  padding: 16px;
}

.product-container {
  align-content: 'center';
  border-bottom: 1px solid #ddd;
  display: flex;
  padding: 16px;
  width: 100%;
}

.product-image {
  flex: 1;
  height: 100px;
  max-width: 100px;
}

.details-wrap {
  padding: 0 16px;
  flex: 3;
}

.remove-button {
  flex: 1;
  margin: auto;
}
</style>