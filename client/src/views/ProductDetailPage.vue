<template>
  <div id="page-wrap" v-if="product">
    <div id="img-wrap">
      <img :src="product.imageUrl" />
    </div>
    <div id="product-details">
      <h1>{{ product.name }}</h1>
      <h3 id="price">${{ product.price }}</h3>
      <p>Average rating: {{ product.averageRating }}</p>
      <button
       @click="addToCart" 
       v-if="!itemInTheCart && !showSuccessMessage" 
       id="add-to-cart"
       >Add to Cart</button>

      <button 
      v-if="!itemInTheCart && showSuccessMessage" 
      id="add-to-cart" 
      class="green-button"
      >Successfully added to cart!</button>

      <button 
      id="add-to-cart"
      class="grey-button"
      v-if="itemInTheCart"
      >Already in the cart!</button>

      <h4>Description:</h4>
      <p>{{ product.description }}</p>
    </div>
  </div>
  <NotFoundPage v-else />
</template>

<script>
import axios from 'axios';
import NotFoundPage from './NotFoundPage.vue';

export default {
  name: "ProductsDetailPage",
  components: { NotFoundPage },
  data() {
    return {
      product: {},
      showSuccessMessage: false,
      cartItems: [],
      inTheCart: false,
    };
  },
  methods: {
    async addToCart() {
      await axios.post('/api/users/123/cart', {
        productId: this.$route.params.id,
      });
      this.showSuccessMessage = true;
      setTimeout(() => {
        this.$router.push('/products');
      }, 1500);
    },
  },
  computed: {
    itemInTheCart() {
      return this.cartItems.some(item => item.id === this.product.id);
  }
  },
  async created() {
    const {data: product} = await axios.get(`/api/products/${this.$route.params.id}`);
    this.product = product;
    
    const {data: cartItems} = await axios.get('/api/users/123/cart');
    this.cartItems = cartItems;
  },
}
</script>

<style scoped>
#page-wrap {
  margin-top: 16px;
  padding: 16px;
  max-width: 600px;
}

#img-wrap {
  text-align: center;
}

img {
  width: 400px;
}

#product-details {
  padding: 16px;
  position: relative;
}

#add-to-cart {
  width: 100%;
}

#price {
  position: absolute;
  top: 24px;
  right: 16px;
}

.green-button {
  background-color: green;
}
.grey-button {
  background-color: grey;
}
</style>
