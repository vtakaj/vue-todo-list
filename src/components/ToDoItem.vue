<template>
    <li class="todo-item"
        v-bind:class="{'done': done}"
        v-on:click="handleClick">
        <span v-if="done">✔</span>
        <!-- {{ text }}を<slot/>に置換 -->
        <slot />
    </li>
</template>
<script>
export default {
    props: {
        /** Text Prop は使用しないので削除する */
        text: { type: String },
        /** Todo の完了ステータスを指定するProp */
        done: { type: Boolean }
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
