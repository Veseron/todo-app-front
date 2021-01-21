<template>
    <li>
        <span v-bind:class="{done: todo.completed}">
            <input type="checkbox" 
                v-on:change="changeStatus()"
                :checked="todo.completed"
                >
            <strong>{{index + 1}}</strong>    
            {{todo.title | uppercase}}
        </span>
        <button v-on:click="$emit('remove-todo', todo._id)"><span>&times;</span></button>
    </li>
</template>

<script>
import TodoList from '@/components/TodoItem'

export default {
    name: 'todo-item',
    props: {
        todo: {
            type: Object,
            required: true
        },
        index: Number,
    },    
    filters: {
        uppercase(value) {
            return value.toUpperCase()
        }
    },
    methods: {
        changeStatus() {
            this.todo.completed = !this.todo.completed
            
            setTimeout(() => {
                this.$emit('change-todo-status', {
                    _id: this.todo._id,
                    completed: this.todo.completed
                }), 100
            })
        }
    }
}
</script>

<style scope>
    li {
        border: 1px solid #ccc;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 1rem 2rem;
        margin-bottom: 1rem;
    }
    strong {
        margin: 0 10px 0 12px;
        font-size: 22px;
    }
    input[type="checkbox"] {
        width: 18px;
        height: 18px;
        cursor: pointer;
    }
    button {
        border: none;
        border-radius: 50%;
        width: 28px;
        height: 28px;
        background-color: rgb(161, 33, 33);
        color: #fff;
        font-size: 20px;
        display: flex;
        justify-content: center;
        align-items: center;
        cursor: pointer;
        transition: ease-in-out .4s;
    }
    button span {
        display: block;
        margin-top: -2.1px;
    }
    button:hover {
        background-color: rgb(129, 25, 25);
    }
    .done {
        text-decoration: line-through;
    }
</style>