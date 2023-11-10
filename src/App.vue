<template>
    <Header title="VUE EXPENSE TRACKER" />
    <Balance :balance="balance" />
    <div class="container">
        <IncomeExpense :income="income" :expense="expense" />
        <TransactionHistory @deleteTrans="deleteTransaction" :transactions="transactions" />
        <AddTransaction @addTransaction="handleAddTransaction" />
    </div>
</template>
<script setup>
import Header from './components/Header.vue';
import Balance from './components/Balance.vue';
import IncomeExpense from './components/IncomeExpense.vue';
import TransactionHistory from './components/TransactionHistory.vue';
import AddTransaction from './components/AddTransaction.vue';
import { ref, computed } from 'vue';

const transactions = ref([
    {
        id: 12,
        title: 'Shopping',
        amount: -200,
    },
    {
        id: 122,
        title: 'Income',
        amount: 2000,
    },
]);

const balance = computed(() => {
    return transactions.value.reduce((accumulator, transaction) => accumulator + transaction.amount, 0);
});

const income = computed(() => {
    return transactions.value
        .filter((tran) => tran.amount > 0)
        .reduce((accumulator, transaction) => accumulator + transaction.amount, 0);
});

const expense = computed(() => {
    return transactions.value
        .filter((tran) => tran.amount < 0)
        .reduce((accumulator, transaction) => accumulator + transaction.amount, 0);
});

const handleAddTransaction = (data) => {
    transactions.value.push({
        id: Math.floor(Math.random() * 1000000),
        title: data.title,
        amount: data.amount,
    });
};

const deleteTransaction = (id) => {
  console.log("id",id)
  transactions.value = transactions.value.filter((transaction)=> transaction.id != id)
}
</script>
