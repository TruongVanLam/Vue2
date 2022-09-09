<script>
import Todo from './components/todo.vue'
import EventHandling from './components/event_handling.vue'
import Binding from './components/binding.vue'
import Props from './components/props.vue'
import Emit from './components/emit.vue'
import ForceUpdate from './components/force_update.vue'
import NextTick from './components/next_tick.vue'
import SlotCustom from './components/slot_custom.vue'
export default {
    components: { Todo, EventHandling, Binding, Props, Emit, ForceUpdate, NextTick, SlotCustom },
    data() {
        return {
            currentTab: 'todo',
            tabs: ['todo', 'event-handling', 'binding'],
            post: {
                id: 1,
                title: 'My life is best than',
                age: 24
            },
            mau: 'green'
        }
    },
    methods: {
        handleChangeColor(color) {
            this.mau = color
        },
        handleChangeAge(age2) {
            this.post.age = age2
        }
    }
}
</script>

<template>
    <div class="demo">
        <button v-for="tab in tabs" :key="tab" :class="['tab-button', {active: currentTab === tab}]"
            @click="currentTab = tab">
            {{ tab }}
        </button>
        <!-- kepp-alive tạo bản sao lưu vào bộ nhớ cache sau khi component được tạo lần đầu tiên  -->
        <keep-alive>
            <component :is="currentTab" class="tab"></component>
        </keep-alive>

        <props :post="post" @change-age="handleChangeAge"></props>
        <p> Age in Parent: {{post.age}}</p>

        <div :style="{color: mau}">
            <emit :post="post" @change_color="handleChangeColor"></emit>
        </div>
        <force-update></force-update>
        <next-tick></next-tick>

        <slot-custom>
            <h2>Slots</h2>
            <h3 slot="header">Here might be a page title</h3>
            <div slot="content">
                <p>A paragraph for the main content.</p>
                <p>And another one.</p>
            </div>
            <p slot="footer">Here's some contact info</p>
        </slot-custom>
    </div>
</template>

<style>
.demo {
    font-family: sans-serif;
    border: 1px solid #eee;
    border-radius: 2px;
    padding: 20px 30px;
    margin-top: 1em;
    margin-bottom: 40px;
    user-select: none;
    overflow-x: auto;
}

.tab-button {
    padding: 6px 10px;
    border-top-left-radius: 3px;
    border-top-right-radius: 3px;
    border: 1px solid #ccc;
    cursor: pointer;
    background: #f0f0f0;
    margin-bottom: -1px;
    margin-right: -1px;
}

.tab-button:hover {
    background: #e0e0e0;
}

.tab-button.active {
    background: #e0e0e0;
}

.tab {
    border: 1px solid #ccc;
    padding: 10px;
}
</style>