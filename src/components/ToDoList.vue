<template>
    <input v-model="inputValue">
    <button v-on:click="handleClick">
        ToDoを追加
    </button>
    <input
        v-model="filterValue"
        placeholder="フィルタテキスト">
    <ul>
        <li v-for="todo in filteredTodoItems"
            v-bind:key="todo.id"
            v-on:click="todo.done = !todo.done">
            <span v-if="todo.done">✔</span> {{ todo.text }}
        </li>
    </ul>
</template>
<script>
export default {
    data() {
        const todoItems = [
            { id: 1, done: false, text: 'Go out to sea' },
            { id: 2, done: false, text: 'Invite the first member' }
        ]
        return { 
            inputValue: '',
            todoItems,
            filteredToDoItems: todoitems, 
            filterValue: '',
        }
    },
    watch: {
        // filterValueの値の変更を監視し
        // filteredTodoItemsを再計算する
        fiteredValue() {
            this.updateFilteredTodoItems()
        },
        // TtpdpOte,sの値の変更を監視し
        // filteredTodoItemsを再計算する
        todoItems: {
            handler() {
                this.updateFilteredTodoItems()
            },
            // 深く監視すすことで配列要素の変更も監視する
            deep: true
        },
    },
    methods: {
        handleClick() {
            // 入力をリストに追加
            this.todoItems.push({
                id: this.todoItems.length + 1,
                text: this.inputValue
            })
            // 入力をクリアする
            this.inputValue = ''
        }
    }
}
</script>
