<script setup>
import { ref, computed } from 'vue'
import { useFetch } from '../js/useFetch'

const baseUrl = 'https://jsonplaceholder.typicode.com/todos/'
const id = ref('1')
const url = computed(() => baseUrl + id.value)

const { data, error, retry } = useFetch(url)
</script>

<template>
    <div>
        <h2>Composables</h2>
        Load post id:
        <button v-for="i in 5" @click="id = i"> {{ i }}</button>

        <div v-if="error">
            <p>Oops! Error encountered: {{error.message}}</p>
            <button @click="retry">Retry</button>
        </div>
        <div v-else-if="data">
            Data loaded:
            <pre>{{ data }}</pre>
        </div>
        <div v-else>Loading...</div>
    </div>
</template>