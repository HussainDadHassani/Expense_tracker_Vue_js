<template>
  <form action="" @submit.prevent="add">
    <h4>Add Transactions: </h4>
    <label for="name">Transaction name: </label>
    <input v-model="text" type="text" class="name" placeholder="Enter Expense ...">
    <label for="amount">Enter the Amount (+ / -): </label>
    <input v-model="amount" type="text" class="amount" placeholder="Enter Amount ...">
    <input type="submit" class="btn" value="Add">
  </form>
</template>
<script setup>
import {ref, defineEmits} from 'vue'
import {useToast} from 'vue-toastification'
const toast = useToast();
const text = ref('')
const amount = ref(null)
const emit = defineEmits(['sent-data'])

const add = () => {
  text.value = text.value.trim()
  amount.value = amount.value.trim()
  if(!text.value || !amount.value) {
    toast.error('this is wrong')
    return
  }
  if(isNaN(+amount.value)) {
    toast.error('Invalid Number!')
    return
  }
  emit('sent-data', {name: text.value, a: +amount.value})
  text.value = null
  amount.value = null
  toast.success('Transaction is added!')
}
</script>


<style scoped>

form input[type="text"] {
  width: 410px;
  margin: 10px 0;
  height: 30px;
  padding-left: 10px;
  font-size: 17px;
  border: 2px solid rgb(32, 48, 127);
  border-radius: 4px;
  outline: none;
}

form label {
  display: block;
  margin-top: 10px;
  font-weight: 16px;
  color:rgb(65, 61, 61);
}

.btn {
  width: 100%;
  margin: 30px auto 0 auto ;
  height: 35px;
  font-size: 17px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  color: white;
  background: rgba(17, 61, 151, 0.991);
}
</style>