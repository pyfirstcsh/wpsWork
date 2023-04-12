<script setup>

import { ref } from 'vue'
const show = ref(false)

</script>
<template>
    <button @click="show = !show"> Change </button>
    <LazyAbundant v-if="show" />
</template>
