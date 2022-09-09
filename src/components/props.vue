<script>
export default {
    data() {
        return {
            post2: {
                id: 2,
                title: 'aaaa',
                age: 1
            }
        }

    },
    props: {
        post: Object
    },
    methods: {
        handleChangeTitle() {
            // Thay đổi giá trị prop tại component con => warning
            this.post = this.post2
            // Dùng emit phát ra 1 event change-age tại component con
            // Tại component cha, hứng sự kiện change-age, sau đó thay đổi giá trị prop tại component cha
            this.$emit('change-age', this.post2.age)
        }
    }
}
</script>

<template>
    <div>
        <h2>Props</h2>
        <p> Age in Children: {{post.age}}</p>
        <button @click="handleChangeTitle">Componet Children: Change age</button>
    </div>
</template>