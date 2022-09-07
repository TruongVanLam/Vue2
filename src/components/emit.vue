<script>
export default {
    props: {
        post: {
            type: Object
        }
    },
    methods: {
        emit(mau) {
            this.$emit('change_color', mau)
        }
    }
}
</script>

<template>
    <div>
        <h2>$Emit</h2>
        <h4>{{post.title}}</h4>
        <button @click="emit('red')">Change color</button>
    </div>
</template>