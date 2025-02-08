<template>
  <h4>Balance is:</h4>
  <p>${{total.toFixed(2)}}</p>
</template>

<script setup>
import {defineProps} from 'vue'
defineProps({
  total: {
    type: Number,
    required: true
  }
})
</script>

<style scoped>
h4 {
  margin-bottom: 10px;
}
</style>