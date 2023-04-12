<script setup>
import { reactive, computed, ref } from 'vue'

const author = reactive({
    name: 'John Doe',
    books: [
        'Vue 2 - Advanced Guide',
        'Vue 3 - Basic Guide',
        'Vue 4 - The Mystery'
    ]
})
const message = ref('')
const text = ref('')
const textareas = ref('')
const checkedNames = ref([])
const picked = ref()
const selected = ref()

const selected_For = ref('A')

const options = ref([
    { id: 1, text: 'One', value: 'A' },
    { id: 2, text: 'Two', value: 'B' },
    { id: 3, text: 'Three', value: 'C' }
])
// 一个计算属性 ref
const publishedBooksMessage = computed(() => {
    return author.books.length > 0 ? 'Yes' : 'No'
})
// 若我们将同样的函数定义为一个方法而不是计算属性，两种方式在结果上确实是完全相同的，
// 然而，不同之处在于计算属性值会基于其响应式依赖被缓存。
// 一个计算属性仅会在其响应式依赖更新时才重新计算。
// 这意味着只要 author.books 不改变，无论多少次访问 publishedBooksMessage 都会立即返回先前的计算结果，而不用重复执行 getter 函数。
</script>

<template>
    <p>Has published books:</p>
    <div>{{ publishedBooksMessage }}</div>
    <p>Message is: {{ message }}</p>
    <input v-model="message" placeholder="edit me" style="display: block;" />

    <p>Text is: {{ text }}</p>
    <input :value="text" @input="event => text = event.target.value" style="display: block;">

    <span>Multiline message is:</span>
    <p style="white-space: pre-line;">{{ textareas }}</p>
    <textarea v-model="textareas" placeholder="add multiple lines"></textarea>

    <div>Checked names: {{ checkedNames }}</div>

    <input type="checkbox" id="jack" value="Jack" v-model="checkedNames">
    <label for="jack">Jack</label>

    <input type="checkbox" id="john" value="John" v-model="checkedNames">
    <label for="john">John</label>

    <input type="checkbox" id="mike" value="Mike" v-model="checkedNames">
    <label for="mike">Mike</label>

    <div>Picked: {{ picked }}</div>

    <input type="radio" id="one" value="One" v-model="picked" />
    <label for="one">One</label>

    <input type="radio" id="two" value="Two" v-model="picked" />
    <label for="two">Two</label>

    <div>Selected: {{ selected }}</div>

    <select v-model="selected">
        <option disabled value="">Please select one</option>
        <option>A</option>
        <option>B</option>
        <option>C</option>
    </select>

    <select v-model="selected_For">
        <option v-for="option in options" :value="option.value" :key="option.id">
            {{ option.text }}
        </option>
    </select>

    <div>Selected: {{ selected }}</div>
</template>