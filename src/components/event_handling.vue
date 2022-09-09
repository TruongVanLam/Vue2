<script>
export default {
    data() {
        return {
            counter: 0
        }
    },
    methods: {
        warn(message, event) {
            if (event)
                console.log(event.target.tagName);
            alert(message)
        },
        handleCounter() {
            return this.counter += 1
        }
    }
}
</script>

<template>
    <div>
        <div>
            <h2>EventHandling</h2>
            <button @click="warn('Hello', $event)">Alert</button><br><br>
        </div>
        <div>
            <button @click="handleCounter()">Đếm cừu</button>
            <p>{{ counter }} con cừu</p>
        </div>
    </div>
</template>