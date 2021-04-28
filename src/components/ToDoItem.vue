<template>
    <li class="todo-item"
        v-bind:class="{'done': done}"
        v-on:click="handleClick">
        <span v-if="done">✔</span> {{ text }}
    </li>
</template>
<script>
export default {
    props: {
        /** ToDoのコンテンツを指定するProp */
        text: {
            // text は文字列 でなければなりません
            type: String
        },
        /** Todo の完了ステータスを指定するProp */
        done: {
            // done は 真偽値 でなければなりません
            type: Boolean
        }
    },
    emits: ['toggle'],
    methods: {
        /** <li>のclickイベントを処理 */
        handleClick() {
            // カスタムイベントtoggleを発行
            this.$emit('toggle')
        }
    }
}
</script>
