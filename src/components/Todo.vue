<script>
let id = 0;
export default {
  //Lifecycle and Template Refs
  mounted(){
    this.$refs.intodo.focus()
  },
  data() {
    return {
      idt: 0,
      msg: "There are ",
      newTodo: "",
      hideCompleted: false,
      todos: [],
    };
  },
  //Computed Property
  computed: {
    filteredTodos() {
      return this.hideCompleted
        ? this.todos.filter((t) => !t.done)
        : this.todos;
    },
  },
  methods: {
    addTodo() {
      this.todos.push({ id: id++, text: this.newTodo, done: false });
      this.idt = id;
      this.newTodo = "";
    },
    removeTodo(todo) {
      this.todos = this.todos.filter((t) => t !== todo);
      id--;
      this.idt = id;
    },
  },
  //Watchers
  watch: {
    idt(i) {
      if(i == 1){
        this.msg = "There is "
      }
      else{
        this.msg = "There are "
      }
    }
  }
};
</script>

<template>
  <!--Conditional & Declarative Rendering-->
  <h4>{{msg}}{{idt}}<span v-if="this.idt != 1"> tasks </span> <span v-else> task </span> </h4>
  <!--Form bindings-->
  <input ref="intodo" v-model="newTodo" @keyup.enter="addTodo" />
  <!--Event Listeners-->
  <button @click="addTodo">Add Todo</button>
  <ul>
    <!--List Rendering-->
    <li v-for="todo in filteredTodos" :key="todo.id">
      <input type="checkbox" v-model="todo.done" />
      <span :class="{ done: todo.done }">{{ todo.text }}</span>
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
  <!--Conditional Rendering-->
  <button @click="hideCompleted = !hideCompleted">
    {{ hideCompleted ? "Show all" : "Hide completed" }}
  </button>
</template>

<style scoped>
.done {
  text-decoration: line-through;
}
</style>
