<template>
  <div>
    <div class="container">
      <ProductItem
        v-for="(product, i) in productList"
        :product-info="product"
        @click:buy="qtyAndamt" />
        <!-- @click:buy="showDetail" /> -->
    </div>
    <hr>
    <br><br>
    <div>
      <p>Total Order by Quantity: {{ totalQty }} pcs; by Amount: {{ totalAmt }} Bth.</p>
      <p>Order categorize by product</p>
      <p>Product A Quantity: {{ aqty }} pcs; Amount: {{ aamt }} Bth.</p>
      <p>Product B Quantity: {{ bqty }} pcs; Amount: {{ bamt }} Bth.</p>
      <p>Product C Quantity: {{ cqty }} pcs; Amount: {{ camt }} Bth.</p>
    </div>
  
    <!-- <h3 v-if="totalOrderPrice">
      Total Order Price: {{ totalOrderPrice }} ฿
    </h3> -->
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

const aqty = bqty = cqty = ref(0)
const aamt = bamt = camt = ref(0)
const totalQty = totalAmt = ref(0)

const qtyAndamt = (product) => {
  if (product.name = "Product A") {
    aqty.value += 1
    aamt.value += 100
  } else if (product.name = "Product B") {
    bqty.value += 1
    bamt.value += 100
  } else if (product.name = "Product C") {
    cqty.value += 1
    camt.value += 100
  } else {
    totalQty.value = aqty.value + bqty.value + cqty.value
    totalAmt.value = aamt.value + bamt.value + camt.value
  }
}

)

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
