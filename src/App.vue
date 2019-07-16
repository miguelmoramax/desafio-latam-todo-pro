<template>
  <div>
    <img class="todo-list-img" :src="img" />
    <list :todos="todos"></list>
  </div>
</template>

<script>
import List from "./List.vue";
export default {
  name: "App",
  components: { List },
  data() {
    return {
      todos: [],
      img:"http://blog.desafiolatam.com/wp-content/uploads/2015/03/desafio-latam-logonegro.png"
    };
  }
};
</script>
<style>
body {
  display: flex;
  flex-flow: row nowrap;
}
.todo-list-img {
  width: 25%;
  height: 25%;
  margin: 0 0 0 5em;
  object-fit: contain;
  display: flex;
  flex-flow: row nowrap;
  align-items: stretch;
}
</style>
