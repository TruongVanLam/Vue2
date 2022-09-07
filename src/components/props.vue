<script>
export default {
    data() {
        return {
            content: ""
        }
    },
    props: {
        post: {
            type: Object,
        }
    },
    methods: {
        handleChangeTitle() {
            return this.post.title = "Update complete!"
        }
    }
}
</script>

<template>
    <div>
        <p> Thang con: {{post.title}}</p>
        <button @click="handleChangeTitle()">Change title con</button>
    </div>
</template>