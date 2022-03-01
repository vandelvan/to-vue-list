<script>
// Components
import Welcome from "./components/Welcome.vue";
import Todo from "./components/Todo.vue";
export default {
  components: {
    Welcome,
    Todo,
  },
  data() {
    return {
      createdby: "vandelvan",
    };
  },
};
</script>

<template>
  <!-- Components -->
  <!-- Props & Emits -->
  <Welcome @response="(msg) => (createdby = msg)" msg="Welcome!" />
  <Todo />
  <br />
  <hr />
  <!-- Emits -->
  <a href="http://vandelvan.github.io/" target="_blank">{{ createdby }}</a>
</template>

<style>
body {
  background-color: #1a1a1a;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ffffff;
  margin-top: 60px;
}
</style>
