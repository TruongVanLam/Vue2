<template>
    <div>
        <h2>$nextTick</h2>
        <ul ref="ul1">
            <li v-for="(item, index) in list" :key="index">{{item}}</li>
        </ul>
        <button @click="addItem">Add item</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            list: ['a', 'b', 'c']
        }
    },
    methods: {
        addItem() {
            this.list.push(`${Date.now()}`)
            this.list.push(`${Date.now()}`)
            this.list.push(`${Date.now()}`)
// thực hiện sau khi dom đã cập nhật 
            this.$nextTick(() => {
                const ulElm = this.$refs.ul1
                console.log(ulElm.childNodes);
                console.log(ulElm.childNodes.length);
            })
        }
    }
}
</script>