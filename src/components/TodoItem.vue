<script>
export default {
    name: "TodoItem",
    props: {
        todo: {
            type: Object,
            required: true,
        },
        index: {
            type: Number,
            required: true,
        },
    },
    methods: {
        toggleComplete() {
            this.$emit("toggle-complete", this.index);
        },
        removeItem() {
            this.$emit("remove-item", this.index);
        },
    },
};
</script>

<template>
    <li>
        <span :class="{ completed: todo.completed }" @click="toggleComplete">
            {{ todo.text }}
        </span>
        <button @click="removeItem">Delete</button>
    </li>
</template>

<style scoped>
.completed {
    text-decoration: line-through;
    color: gray;
    cursor: pointer;
}

li {
    display: flex;
    justify-content: center;
    gap: 10px;
    align-items: center;
}

li span {
    cursor: pointer;
    flex-grow: 1;
    border: 1px solid #ccc;
    height: 30px;
    display: flex;
    justify-content: center;
    align-items: center;
}

li button {
    cursor: pointer;
    border: none;
    background-color: red;
}
</style>
