<template>
    <div>
        // JavaScript expressions in Vue are enclosed in double curly brackets.
        <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
        <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>

        <todo  v-for="todo in todos" :todo="todo" :key="todo.id"
        v-on:delete-todo="deleteTodo"></todo>
    </div>
</template>

<script type = "text/javascript" >
    import Todo from '@/components/Todo';

    export default {
        name: "TodoList",
        components: {Todo},
        props: ['todos'],
        methods: {
            deleteTodo(todo) {
                const todoIndex = this.todos.indexOf(todo);
                this.todos.splice(todoIndex, 1);
            },
        },
    };
</script>
