<template>
    <h2>{{ title }}</h2>
</template>
<script setup>

const props = defineProps({
    title : {
        default : "tracker",
        type : String
    }
})


</script>
