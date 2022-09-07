<script>
export default {
    data() {
        return {
            modeUpdate: false,
            newTodoText: '',
            todo: {
                id: Number,
                title: String
            },
            todos: [
                {
                    id: 1,
                    title: 'Do the dishes'
                },
                {
                    id: 2,
                    title: 'Take out the trash'
                },
                {
                    id: 3,
                    title: 'Mow the lawn'
                }
            ],
            nextTodoId: 4
        }
    },
    methods: {
        submitForm() {
            !this.modeUpdate ? this.addNewTodo() : this.updateTodo()
        },
        addNewTodo() {
            console.log('add');
            if (this.newTodoText) {
                this.todos.push({
                    id: this.nextTodoId++,
                    title: this.newTodoText
                })
                this.newTodoText = ''
            }
        },
        updateTodo() {
            console.log('update');
            if (this.newTodoText) {
            this.todos.find(el => el.id === this.todo.id).title = this.newTodoText
            this.modeUpdate = false
            this.newTodoText = ''
            }
        },
        handleRemove(id) {
            this.todos = this.todos.filter(el => el.id != id)
        },
        handleUpdate(id) {
            this.todo = this.todos.find(el => el.id === id)
            this.modeUpdate = true
            this.newTodoText = this.todo.title

        }
    }
}
</script>
    
<template>
    <div>
        <h2>Bai Tap ToDo</h2>
        <form v-on:submit.prevent="submitForm">
            <label for="new-todo">Add a todo</label>
            <input v-model="newTodoText" id="new-todo" placeholder="E.g. Feed the cat" />
            <button>Submit</button>
        </form>
        <ul v-for="(todo, index) in todos" :key="todo.id" :title="todo.title" @remove="todos.splice(index, 1)">
            <li>
                {{todo.title}}
                <div>
                    <button @click="handleUpdate(todo.id)">Update</button> &nbsp;
                    <button @click="handleRemove(todo.id)">Remove</button>
                </div>

            </li>
        </ul>
    </div>
</template>