<template>
  <Header />
  <p>{{ d }}</p>
  <div class="container">
    <TotalBalance :total="total" />
    <IncomExp :income="income" :expense="expense" />
    <History :transactions= "transactions" @dlt="dlt"/>
    <AddExpense @sent-data="show" />
  </div>
</template>

<script setup>
import Header from "./components/HeaderCom.vue";
import TotalBalance from './components/TotalExpense.vue'
import History from './components/ExpenseList.vue'
import AddExpense from './components/AddExpense.vue'
import IncomExp from './components/IncomeExpense.vue'
import { ref, computed } from 'vue'
// ARRAY OF THE TRANSACTION LIST
const transactions = ref([])

// TOTAL
const total = computed(() => {
  return transactions.value.reduce((acc, t) => {
    return acc + t.amount
  }, 0)
})
// INCOME
const income = computed(() => {
  return transactions.value.filter(t => t.amount > 0).reduce((acc, t) => {
    return acc + t.amount
  }, 0)
})
// EXPENSE
const expense = computed(() => {
  return transactions.value.filter(t => t.amount < 0).reduce((acc, t) => {
    return acc + t.amount
  }, 0)
})
// ADDING TRANSACTION
const d = ref('')
const show = (data) => {
  let id = Math.floor(Math.random() * 100000000)
  const tr = {id: id, name: data.name, amount: data.a}
  transactions.value.push(tr)
}
// DELETING A TRANSCATION FROM LIST
const dlt = (d) => {
  transactions.value = transactions.value.filter((tr) => tr.id != d.id)
}
</script>

<style>
body {
  height: 100vh;
  width: 100vw;
  display: flex;
  justify-content: center;
  align-items: center;
  font-family:  Arial, Helvetica, sans-serif;
}

.container {
  width: 420px;
}
</style>
