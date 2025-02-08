<template>
  <div class="card">
    <div class="income">
      <p>Income</p>
      ${{ income.toFixed(2) }}
    </div>
    <div class="expense">
      <p>Expense</p>
      ${{ expense.toFixed(2) }}
    </div>
  </div>
</template>

<script setup>
import { defineProps } from "vue";
defineProps({
  income: {
    type: Number,
    required: true,
  },
  expense: {
    type: Number,
    required: true,
  },
});
</script>


<style scoped>
.card {
  display: flex;
  padding: 10px;
  box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.1);
  border-radius: 10px;
  margin-top: 10px;
}
.card p {
  margin-bottom: 10px;
}
.income,
.expense {
  width: 50%;
  text-align: center;
  margin-bottom: 10px;
  color: rgb(181, 23, 23);
}
.income {
  border-right: 2px solid rgba(183, 173, 173, 0.416);
  color: green;
}
.income p {
  color: black;
}
.expense p {
  color: black;
}
</style>