<template>
    <div class="todoListContainer">
        <div v-for="(todo, index) in todos" :key="index" class="todoContainer">
            <TodoItem v-bind:todo="todo" v-bind:index="index" v-on:deleteTodo="$emit('deleteTodo', index)"/>
        </div>
    </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";
export default {
    name: "TodoList",
    components: {
        TodoItem
    },
    props: ["todos"]
}
</script>

<style scoped>
    .todoContainer {
        border: 1px solid rgba(0,0,0,.125);
        border-radius: 5px;
        margin: 5px;
    }
    .todoContainer:nth-child(even) {
        background: #f9f9f9;
    }
    .todoContainer:nth-child(odd) {
        background: rgb(201, 199, 199);
    }
    .todoListContainer {
        width: 450px;
        margin: auto;
        font-size: 18px;
    }
</style>
