<template>
  <Header/>
  <Balance/>
  <div class="container">
      <IncomeExpense/>
      <TransactionHistory :transactions="transactions" />
      <AddTransaction/>
  </div>
</template>
<script setup>
  import Header from './components/Header.vue';
  import Balance from './components/Balance.vue';
  import IncomeExpense from './components/IncomeExpense.vue';
  import TransactionHistory from './components/TransactionHistory.vue';
  import AddTransaction from './components/AddTransaction.vue';
  import { ref } from 'vue';

  const transactions = ref([{
    id: 12,
    title : "Shopping",
    amount : -20
  }])

</script>