<script setup>
const counter = useCounter()

</script>
<template>
    Counter: {{ counter }}
    <button @click="counter++">
        +
    </button>
    <button @click="counter--">
        -
    </button>
</template>
