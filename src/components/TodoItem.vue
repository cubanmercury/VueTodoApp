<template>
    <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
        <p>
            <input type="checkbox" v-on:change="markComplete" />    
            {{todo.title}}
            <button @click="$emit('del-todo', todo.id)" class="del"><i class="fas fa-trash-alt"></i></button>
        </p>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todo"],
    methods: {
        markComplete() {
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>


<style scoped>
    .todo-item{
        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px dotted #ccc;
        border-radius: 5px;
        margin: 5px 0;
    }
    .is-complete{
        text-decoration: line-through;
    }
    .del{
        color: #ff0000;
        border: none;
        cursor: pointer;
        float: right;
    }
</style>
