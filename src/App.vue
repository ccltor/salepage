<template>
  <div>
    <div class="container">
      <ProductItem
        v-for="(product, i) in productList"
        :product-info="product"
        @click:buy="showDetail" />
    </div>
    <hr>
    <br><br>
    <h3 v-if="totalOrderPrice">
      Total Order Price: {{ totalOrderPrice }} ฿
    </h3>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import ProductItem from './components/ProductItem.vue';

const productList = ref([
  {
    name: 'Product A',
    price: 100,
    quantity: 99,
  },
  {
    name: 'Product B',
    price: 200,
    quantity: 99,
  },
  {
    name: 'Product C',
    price: 300,
    quantity: 99,
  }
])
const totalOrderPrice = ref(0)
// const selectedProducts = ref([])

const showDetail = (product) => {
  totalOrderPrice.value += Number(product.price)
  // selectedProducts.value.push(product)
}

</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>

<style scoped>
.container {
  display: flex;
  padding: 16px;
  gap: 8px;
}
</style>
