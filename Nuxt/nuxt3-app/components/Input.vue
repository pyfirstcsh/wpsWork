<script setup>

import { ref } from 'vue'
const context = ref('')
const text = ref('')
const sumbit = () => {
    alert(context.value)
}
</script>

<template>
    <p>Text is: {{ context }}</p>
    <input v-model="context" style="display: block;" @keyup.enter="sumbit">
</template>