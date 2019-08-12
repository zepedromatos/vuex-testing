<template>
  <div>
    <h1>Todos</h1>
    <AddTodo />
    <Todos />
  </div>
</template>

<script>
import Todos from "./Todos";
import AddTodo from "./AddTodo";
export default {
  name: "Home",
  components: {
    Todos,
    AddTodo
  }
};
</script>

<style lang="scss" scoped>
div {
  display: grid;
  justify-content: center;
  justify-items: center;

  h1 {
    margin-top: 1rem;
  }
}
</style>