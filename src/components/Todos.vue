<template>
  <div class="todos">
    <div class="todos__wrapper">
      <v-card dark color="primary" v-for="todo in allTodos" :key="todo.id" xs4>
        <v-card-text>{{ todo.title }}</v-card-text>
        <div class="todos__completed-wrapper" @click="updateThisTodo(todo)">
          <input
            type="checkbox"
            name="completed"
            id="completed"
            v-model="todo.completed"
            class="todos__completed-checkbox"
          />
          <span class="todos__completed-text" v-if="todo.completed">Completed</span>
          <span
            class="todos__completed-text todos__completed-text--not-completed"
            v-if="!todo.completed"
          >Not Completed</span>
        </div>
        <i class="far fa-trash-alt delete-icon" @click="deleteTodo(todo.id)"></i>
      </v-card>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";

export default {
  name: "Todos",
  methods: {
    ...mapActions(["fetchTodos", "deleteTodo", "updateTodo"]),
    updateThisTodo(todo) {
      const updTodo = {
        id: todo.id,
        title: todo.title,
        completed: !todo.completed
      };
      this.updateTodo(updTodo);
    }
  },
  computed: {
    ...mapGetters(["allTodos"])
  },
  created() {
    this.fetchTodos();
  }
};
</script>

<style lang="scss" scoped>
.todos {
  width: 85%;
  margin: 0 auto;
  display: grid;
}

.todos__wrapper {
  margin-top: 4rem;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-column-gap: 5vw;
  grid-row-gap: 1rem;
}

.todos__completed-wrapper {
  margin: 0 auto 1rem auto;
  width: 70%;
  display: grid;
  justify-content: center;
  align-content: center;
  align-items: center;
  grid-auto-flow: column;
  cursor: pointer;
}

.todos__completed-text {
  margin-left: 1rem;
}

.delete-icon {
  position: absolute;
  bottom: 1rem;
  right: 1rem;
  cursor: pointer;
}
</style>