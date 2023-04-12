<script setup>
import { reactive, ref } from 'vue'

const myObject = reactive({
    title: 'How to do lists in Vue',
    author: 'Jane Doe',
    publishedAt: '2016-04-10'
})
const parentMessage = ref('Parent')
const items = ref([{ message: 'Foo' }, { message: 'Bar' }])

</script>

<template>
    <ul>
        <li v-for="(value, key, index) in myObject" :key="key">
            {{ index }}. {{ key }}: {{ value }}
        </li>
    </ul>
    <ul>
        <li v-for="(item, index) in items" :key="index">
            {{ parentMessage }} - {{ index }} - {{ item.message }}
        </li>
    </ul>
</template>