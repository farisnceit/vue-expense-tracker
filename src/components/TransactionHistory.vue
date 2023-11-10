<template>
    <h3>History</h3>
    <ul id="list" class="list">
    <li v-for="transaction in transactions" :key="transaction.id" :class="transaction.amount >= 0 ? 'plus' : 'minus'">
        {{ transaction.title }} <span>${{ transaction.amount }}</span><button @click="handleDelete(transaction.id)" class="delete-btn">x</button>
    </li> 
    
    <span v-if="transactions.length == 0">Add Expense or Income</span>

    </ul>
</template>
<script setup>

    

    const props = defineProps({
        transactions: {
            type: Array,
            required: true,
        },
    })

    const emit = defineEmits(['deleteTrans'])

    const handleDelete = (transId) => {
        
        let text = "Are you sure you want to delete ?";
        if (confirm(text) == false) {
            return
        } 

        emit('deleteTrans',transId)
    }

</script>