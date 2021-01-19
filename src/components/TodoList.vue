<template>
    <div>
        <h2>Todo List on 17.01.2021</h2>
        <ul>  
            <TodoItem
                v-for="(todo, index) of todos"
                v-bind:todo="todo"
                v-bind:index="index"
                v-bind:key="index"
                @remove-todo="removeTodo"
            />
        </ul>
    </div>
</template>

<script>
import TodoItem from "@/components/TodoItem";

export default {
    name: 'todo-list',
    props: ['todos'],
    components: {
        TodoItem: TodoItem,
    },
    methods: {
        removeTodo(id) {
            this.$emit('remove-todo', id)
        }
    }
}
</script>

<style scoped>
    ul {
        list-style: none;
    }
</style>