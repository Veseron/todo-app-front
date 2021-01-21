<template>
    <div>
        <ul>  
            <TodoItem
                v-for="(todo, index) of todos"
                :todo="todo"
                :index="index"
                :key="index"
                @change-todo-status="changeStatus"
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
        },
        changeStatus(todo) {
            this.$emit('change-status', todo) 
        }
    }
}
</script>

<style scoped>
    ul {
        list-style: none;
    }
</style>