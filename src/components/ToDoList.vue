<template>
    <input v-model="inputValue">
    <button v-on:click="handleClick">
        ToDoを追加
        </button>
        <input
        v-model="filterValue"
        placeholder="フィルタテキスト">
    <ul>
        <ToDoItem
            v-for="todo in filteredTodoItems"
            v-bind:key="todo.id"
            v-bind:done="todo.done"
            v-on:toggle="todo.done = !todo.done">
            <b>{{ todo.text }}</b>
        </ToDoItem>
    </ul>
</template>
<script>
import ToDoItem from './ToDoItem.vue'

export default {
    components: { ToDoItem },
    data() {
        const todoItems = [
            { id: 1, done: false, text: 'Go out to sea' },
            { id: 2, done: false, text: 'Invite the first member' },
        ]
        return { 
            inputValue: '',
            todoItems,
            filteredTodoItems: todoItems,
            filterValue: '',
        }
    },
    computed: {
        filteredTodoItems() {
            if (!this.filterValue) {
                return this.todoItems
            }
            return this.todoItems.filter((todo) => {
                return todo.text.includes(this.filterValue)
            })
        }
    },
    methods: {
        handleClick() {
            // 入力をリストに追加
            this.todoItems.push({
                id: this.todoItems.length + 1,
                done: false,
                text: this.inputValue
            })
            // 入力をクリアする
            this.inputValue = ''
        },
    }
}
</script>
<style scoped>
.todo-item.done {
    /* 背景を緑色にする */
    background-color: #3fb983;
    color: #ffffff;
}
</style>