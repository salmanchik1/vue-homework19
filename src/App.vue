<script>
import TodoList from "./components/TodoList.vue";

export default {
    name: "App",
    components: {
        TodoList,
    },
};
</script>

<template>
    <div id="app">
        <todo-list />
    </div>
</template>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}

</style>