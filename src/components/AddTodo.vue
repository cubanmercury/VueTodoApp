<template>
    <div class="add-todo-container">
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add Todo ..." />
            <input type="submit" value="submit" class="btn" />
        </form>
    </div>
</template>

<script>
//import uuid from 'uuid';
export default {
    name: "AddTodo",
    data() {
        return{
          title: ''  
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();
            const newTodo = {
                title: this.title,      //json placeholder assigns an id to each todo when the post request is made
                completed: false
            }
            //send up to parent
            this.$emit('add-todo', newTodo);
            this.title = '';
        }
    }
}
</script>

<style scoped>
    form{
        display: flex;
    }
    input[type="text"]{
        flex: 10;
        padding: 5px;
    }
    input[type="submit"]{
        flex: 2;
    }
    .add-todo-container{
        width: 100%;
        margin: 50px 0 15px 0; 
    }
</style>
