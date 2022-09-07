<template>
    <div>
        <h2>$ForceUpdate</h2>
        <div>
            Name: {{ person.name }}
        </div><br>
        <div>
            Nick name: {{ person.nickname }}
        </div><br>
        <div>
            <button @click="changeName">Change Name</button>
        </div><br>
        <div>
            <button @click="changeNickname">Change Nick Name</button>
        </div><br>
        <div>
            <button @click="changeNicknameProperly">Change Nick name properly</button>
        </div>
    </div>
</template>

<script>
import Vue from 'vue'
export default {
    data() {
        return {
            person: {
                name: 'Edson'
            }
        }
    },
    methods: {
        changeName() {
            this.person.name = 'Arantes';
        },
        changeNickname() {
            this.person.nickname = Math.random().toString(36).substring(7);
            this.$forceUpdate();
        },
        changeNicknameProperly() {
            Vue.set(this.person, 'nickname', 'Louis');
            this.$forceUpdate();
        }
    }
}
</script>
