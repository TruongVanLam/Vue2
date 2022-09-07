<script>
import Todo from './components/todo.vue'
import Counter from './components/counter.vue'
import EventHandling from './components/event_handling.vue'
import Binding from './components/binding.vue'
import Props from './components/props.vue'
import Emit from './components/emit.vue'
import ForceUpdate from './components/force_update.vue'
import NextTick from './components/next_tick.vue'
export default {
    components: { Todo, Counter, EventHandling, Binding, Props, Emit, ForceUpdate, NextTick },
    data() {
        return {
            post: {
                id: 1,
                title: 'My life is best than',
            },
            favorited: true,
            mau: 'green'
        }
    },
    methods: {
        handleChangeColor(color) {
            this.mau = color
        }
    }
}
</script>

<template>
    <div>
        <todo></todo>
        <counter></counter>
        <event-handling></event-handling>
        <br />
        <binding></binding>
        <props v-bind:post="post"></props>
        <button @click="post.title = 'update'">Change title cha</button>
        <p> Thang cha: {{post.title}}</p>
        <div :style="{color: mau}">
            <emit :post="post" @change_color="handleChangeColor"></emit>
        </div>
        <force-update></force-update>
        <next-tick></next-tick>
    </div>
</template>
