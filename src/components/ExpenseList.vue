<template>
  <p>History</p>
  <ul class="list">
    <li :class="t.amount > 0 ? 'plus' : 'minus'" v-for="t in transactions" :key="t.id">
      {{t.name}} <span>${{ t.amount.toFixed(2) }}</span>
      <button @click="removeTr(t.id)" class="dlt-btn">X</button>
    </li>
  </ul>
</template>
<script setup>
import {defineProps, defineEmits} from 'vue'

const emit = defineEmits(['dlt'])

defineProps({
  transactions: {
    type: Array,
    required: true
  }
})

const removeTr = (id) => {
  emit('dlt', {
    id: id
  })

}

</script>


<style scoped>
p {
  width: 100%;
  font-weight: bold;
  margin: 10px 0 0 0;
}

.list {
  width: 100%;
  padding: 10px 0;
  border-top: 1px solid;
  border-bottom: 1px solid;
  transition: all 1s ease;
}

.list li {
  list-style: none;
  height: 35px;
  box-shadow: 1px 1px 10px rgba(0, 0,0, 0.2);
  line-height: 35px;
  position: relative;
  padding: 0 10px;
  display: flex;
  justify-content: space-between;
  border-radius: 3px;
  margin-bottom: 3px;
  cursor: pointer;
}

.dlt-btn {
  transition: all .7s ease-in;
  position: absolute;
  top: 0;
  left: -35px;
  height: 35px;
  width: 35px;
  cursor: pointer;
  background: rgb(141, 49, 49);
  border: none;
  opacity: 0;
  color: white;
  border-radius: 4px;
  font-weight: bold;
}

.list li:hover > .dlt-btn {
  opacity: 1;
}

.plus {
  border-right: 4px solid green;
}

.minus {
  border-right: 4px solid red;
}
</style>