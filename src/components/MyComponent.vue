<template>
  <div class="content">
    {{ msg }}
    <button @click="updateMessage()">
      update
    </button>
  </div>
</template>

<script setup>
const props = defineProps({
  msg: {
    type: String,
    // default: 'Vue Component',
    required: true
  }
})

const emit = defineEmits([
  'update:message'
])

const updateMessage = () => {
  emit('update:message', 'Updated Message')
}

</script>

<style scoped>
.content {
  width: fit-content;
  border-radius: 4px;
  border: 1px solid black;
  padding: 16px;
  margin-top: 16px;
}
</style>
