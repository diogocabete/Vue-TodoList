<template>
    <div class="addTodoContainer">
        <input type="text" v-model="newTodo" placeholder="Add Todo" @keyup.enter="addTodo">
        <button @click="addTodo" class="addBtn">Add Todo</button>
    </div>
</template>

<script>
export default {
    name: "AddTodo",
    props: ["todos"],
    data() {
        return {
            newTodo: ''
        }
    },
    methods: {
        addTodo() {
            if(this.newTodo === ''){
                alert("Todo can't be empty")
            } else {
                this.todos.push({title: this.newTodo, completed: false})
                this.newTodo = ''
            }

        }
    }
}
</script>

<style scoped>
input[type="text"] {
    padding: 8px 2px;
    margin-right: 1em;
    margin-bottom: 1em;
    font-size: 18px;
}

button {
    color: white;
    padding: 10px;
    background: #007bff;
    border: none;
    border-radius: 5px;
    outline:none;
    cursor: pointer;
    font-size: 18px;
}
</style>
