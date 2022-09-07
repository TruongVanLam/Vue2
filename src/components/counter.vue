<script>
export default {
    data() {
        return {
            counter: 0
        }
    },
    methods: {
        handleCounter() {
            return this.counter += 1
        }
    }
}
</script>
<template>
    <div>
        <button @click="handleCounter()">Đếm cừu</button>
        <p>{{ counter }} con cừu</p>
    </div>
</template>