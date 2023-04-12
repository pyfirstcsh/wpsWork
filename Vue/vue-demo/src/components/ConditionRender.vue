<script setup>
import { ref } from 'vue'
const awesome = ref(true)

</script>
<template>
    <button @click="awesome = !awesome" style="display: block;">Toggle</button>
        <h1 v-if=" awesome">Vue is awesome!</h1>
        <h1 v-else>Oh no 😢</h1>
        <div v-if="awesome">
            <p>Paragraph 1</p>
            <p>Paragraph 2</p>
        </div>
        <div v-else>
            <p>Paragraph 3</p>
            <p>Paragraph 4</p>
        </div>
        <template v-if="awesome">
            <p>Paragraph A</p>
            <p>Paragraph B</p>
        </template>
        <template v-else>
            <p>Paragraph C</p>
            <p>Paragraph D</p>
        </template>
</template>                             

