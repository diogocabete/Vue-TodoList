<template>
    <div class="todoItemContainer">
        <input type="checkbox" v-bind:checked='todo.completed' @change="changeChecked(todo)"> 
        <div :class="[todo.completed ? 'completed' : '']">{{todo.title}}</div>
        <button @click="$emit('deleteTodo', index)" class="del"><i class="far fa-trash-alt"></i></button>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todo","index"],
    methods: {
        changeChecked() {
            this.todo.completed = !this.todo.completed
        }
    }
}
</script>

<style scoped>
    .completed {
        text-decoration: line-through;
    }
    .todoItemContainer {
        display: grid;
        grid-template-columns: 10% 80% 10%;
        padding: 12px;
    }
    .del {
        cursor: pointer;
        bordeR: none;
        background: none;
        outline:none;
    }
    .del:hover {
        color: red;
    }
</style>
