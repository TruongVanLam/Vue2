<script>
export default {
    methods: {
        warn(message, event) {
            if (event)
                console.log(event.target.tagName);
            alert(message)
        },
        handleScroll() {
            alert('Ban dang cuon trang')
        }
    }
}
</script>

<template>
    <div @scroll.passive="handleScroll()">
        <button @click.once="warn('Hello', $event)">Click me</button>
    </div>
</template>