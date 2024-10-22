<template>
  <div class="product-item">
    <h2>{{ props.productInfo.name }}</h2>
    <p> ฿ {{ props.productInfo.price }}</p>
    <button @click="buyProduct()">
      Buy
    </button>
  </div>
</template>

<script setup>
const props = defineProps({
  productInfo: {
    type: Object,
    default: () => ({
      name: '',
      price: 0,
      quantity: 1,
    })
  },
  // title: {

  // },
  // name: {

  // },
  // price: {

  // }
})

const emit = defineEmits([
  'click:buy'
])

const buyProduct = () => {
  emit('click:buy', props.productInfo)
}


</script>

<style scoped>
.product-item {
  width: 200px;
  height: 200px;
  border: 1px solid black;
  border-radius: 8px;
  padding: 4px 8px;
}
</style>
