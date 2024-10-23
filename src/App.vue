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
    <div v-if ="totalAmt">
      <h3>Total Order by Quantity: {{ totalQty }} pcs; by Amount: {{ totalAmt }} Bth.</h3>
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

const aqty = ref(0)
const bqty = ref(0)
const cqty = ref(0)
const aamt = ref(0)
const bamt = ref(0)
const camt = ref(0)
const totalQty = ref(0)
const totalAmt = ref(0)

const qtyAndamt = (selectedProduct) => {
  console.log("selecetdProduct =", selectedProduct)
  console.log("selecetdProduct.name =", selectedProduct.name)
  console.log("condition result= ", (selectedProduct.name == "Product A"))
  console.log("condition result= ", (selectedProduct.name == "Product B"))
  console.log("condition result= ", (selectedProduct.name == "Product C"))

  if (selectedProduct.name == "Product A") {
    aqty.value += 1
    aamt.value += 100
  } else if (selectedProduct.name == "Product B") {
    bqty.value += 1
    bamt.value += 200
  } else if (selectedProduct.name == "Product C") {
    cqty.value += 1
    camt.value += 300
  } else {
    //
  }
  totalQty.value = aqty.value + bqty.value + cqty.value
  totalAmt.value = aamt.value + bamt.value + camt.value
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
