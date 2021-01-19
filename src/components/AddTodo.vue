<template>
    <form @submit="submitHandler">
        <input v-model="formData.title" name="title" type="text" placeholder="Enter todo">
        <input type="submit" value="Create todo">
    </form>
</template>

<script>
export default {
    data() {
        return {
            formData: {
                title: ""
            }
        }
    },
    methods: {
        submitHandler(e) {
            e.preventDefault()
                
            if (this.formData.title.trim()) {

                const newTodo = {
                    id: Date.now(),
                    title: this.formData.title,
                    completed: false
                }

                this.$emit('add-todo', newTodo) 
                this.formData.title = ""
            }    
        }
    }
}
</script>

<style scoped>

form {
    margin: 15px 0 25px 0;
    display: flex;
    justify-content: center;
    height: 44px;
}

input[type="text"] {
    border-radius: 0;
    outline: none;
    border: 1px solid #ccc;
    padding: 10px 12px;
    font-size: 20px;
}
input[type="submit"] {
    border: none;
    font-size: 18px;
    padding: 10px 16px;
    border-radius: 1px solid #000;
    background-color: #000;
    color: #fff;
    height: 100%;
    cursor: pointer;
}
@media screen and (max-width: 492px) {
    form {
        display: grid;
        grid-template-columns: 65% 35%;
    }
}
</style>