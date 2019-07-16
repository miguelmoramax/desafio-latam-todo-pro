<template id="todo-list">
  <section class="todos">
    <h1>
      Tareas
    </h1>
    <div class="todos__new input-group">
      <input
        type="text"
        class="input-group-field"
        v-model="newtodo"
        @keyup.enter="addtodo"
        placeholder="Nueva tarea"
      />
      <span class="input-group-button">
        <button @click="addtodo" class="button">
          <i class="fa fa-plus"></i> Añadir
        </button>
      </span>
    </div>

    <div class="todos__clear button-group pull-right">
      <button @click="clearCompleted">
        <i class="fa fa-check"></i> Limpiar Completedas
      </button>
      <button @click="clearAll">
        <i class="fa fa-trash"></i> Limpiar Todas
      </button>
    </div>

      <items
        v-for="(todo, index) in todos"
        @remove="removetodo(index)"
        @complete="completetodo(todo)"
        :todo="todo"
        :key="index"
      ></items>
  </section>
</template>

<script>
import Items from "./Items.vue";
export default {
  name: "list",
  components: { Items },
  props: {
    todos: { default: [] }
  },
  data() {
    return {
      newtodo: ""
    };
  },
  methods: {
    addtodo() {
      if (this.newtodo) {
        this.todos.push({
          title: this.newtodo,
          completed: false
        });
        this.newtodo = "";
      }
    },
    completetodo(todo) {
      todo.completed = !todo.completed;
    },
    removetodo(index) {
      this.todos.splice(index, 1);
    },
    clearCompleted() {
      this.todos = this.todos.filter(this.inProgress);
    },
    clearAll() {
      this.todos = [];
    },

    inProgress(todo) {
      return !this.isCompleted(todo);
    },
    isCompleted(todo) {
      return todo.completed;
    }
  }
};
</script>
<style>
.todos {
  width: 100%;
  padding: 1em;
  margin: 1em auto;
  overflow: auto;
  background-color: white;
}

.todos__list {
  clear: both;
}
li {
    list-style-type: none;
}
</style>
