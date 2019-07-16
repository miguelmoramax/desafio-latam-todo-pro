<template id="todo-item">
  <li class="todos__item">
    <button :class="className" @click.self="$emit('complete')">{{ todo.title }}</button>
    <button class="todos__item__remove" @click="$emit('remove')">
      <i class="fa fa-times"></i>
    </button>
  </li>
</template>
<script>
export default {
  name: "items",
  props: ["todo"],
  computed: {
    className() {
      let classes = ["todos__item__toggle"];
      if (this.todo.completed) {
        classes.push("todos__item__toggle--completed");
      }
      return classes.join(" ");
    }
  }
};
</script>

<style>
.todos__item {
  margin: .5em 0 .5em 0;
  position: relative;
}

.todos__item__toggle {
  cursor: pointer;
  width: 100%;
  text-align: left;
  padding: 0.85em 2.25em 0.85em 1em;
  background-color: lightblue;
  border: 0.1px solid black;
}

.todos__item__toggle--completed {
  text-decoration: line-through;
}
.todos__item__remove {
  position: absolute;
  height: 100%;
  top: 50%;
  right: 0;
  transform: translateY(-50%);
}
.todos__item__remove i {
  vertical-align: middle;
}
</style>
