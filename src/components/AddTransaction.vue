<template>
     <h3>Add new transaction</h3>
      <form id="form" @submit.prevent="onFormSubmit">
        <div class="form-control">
          <label for="text">Text</label>
          <input type="text" id="text" v-model="transText" placeholder="Enter text..." />
        </div>
        <div class="form-control">
          <label for="amount"
            >Amount <br />
            (negative - expense, positive - income)</label
          >
          <input type="number" id="amount" v-model="amount" placeholder="Enter amount..." />
        </div>
        <button class="btn">Add transaction</button>
      </form>
    
</template>
<script setup>

import { ref } from 'vue';

const emit = defineEmits(['addTransaction']);

const transText = ref('');
const amount = ref('');


const onFormSubmit = () => {
  
  if (transText.value =="" || amount.value ==""){
    alert("Fill Both Fields");
    return;
  }

  const transactionData = {
    title: transText.value,
    amount: parseFloat(amount.value),
  };

  transText.value = "";
  amount.value = "";

  emit("addTransaction",transactionData);
}




</script>