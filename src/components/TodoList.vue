<script>
import TodoItem from "./TodoItem.vue";

export default {
    name: "TodoList",
    components: {
        TodoItem,
    },
    data() {
        return {
            newTodo: "",
            todos: [],
        };
    },
    methods: {
        addTodo() {
            if (this.newTodo.trim()) {
                this.todos.push({ text: this.newTodo, completed: false });
                this.newTodo = ""; // Clear the input
            }
        },
        removeTodo(index) {
            this.todos.splice(index, 1);
        },
        toggleComplete(index) {
            this.todos[index].completed = !this.todos[index].completed;
        },
    },
};
</script>

<template>
    <div class="container">
        <h1>Todo List</h1>
        <div class="input-container">
            <input
                v-model="newTodo"
                placeholder="Enter a new task"
                @keyup.enter="addTodo"
            />
            <button @click="addTodo">Add</button>
        </div>
        <ul>
            <todo-item
                v-for="(todo, index) in todos"
                :key="index"
                :todo="todo"
                :index="index"
                @toggle-complete="toggleComplete"
                @remove-item="removeTodo"
            ></todo-item>
        </ul>
    </div>
</template>

<style>
.container {
    max-width: 500px;
    margin: 0 auto;
    padding: 20px;
    background-color: #f5f5f5;
    border-radius: 5px;
}

.input-container {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
}

input {
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    flex-grow: 1;
}

button {
    padding: 10px 20px;
    background-color: #4caf50;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

ul {
    list-style-type: none;
    padding: 0;
    display:flex;
    flex-direction: column;
    gap: 10px;
}

</style>
