<script>
export default {
  // declare emitted events
  emits: ['response'],
  created() {
    // emit with argument
    this.$emit('response', 'Coded by Ivan Orozco')
  },
  data() {
    return {
      logoClass: "logo",
    };
  },
  //Props
  props: {
    msg: String,
  },
};
</script>

<template>
  <!--Attribute Bindings-->
  <h1>
    To-<img :class="logoClass" alt="Vue logo" src="../assets/logo.png" />ue List
  </h1>
  <!--Declarative Rendering-->
  <h2>{{ msg }}</h2>

  <p>To use this site just start by adding to-dos below</p>

  <p>
    <a href="https://github.com/vandelvan/to-vue-list" target="_blank">
      Github Repo
    </a>
  </p>
</template>

<style>
.logo {
  height: 25px;
  width: 25px;
}
a {
  color: #42b983;
}
</style>
