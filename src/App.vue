<template>
  <h1>Todos</h1>

  <ul>
    <li
      :class="{ completed: todo.completed }"
      v-for="todo in todos"
      :key="todo.id"
      @click="toggleItemState(todo.id)"
    >
      {{ todo.title }}
    </li>
  </ul>

  <input
    type="text"
    v-model="item"
    placeholder="Todo Item"
    @keyup.enter="addItem"
  />
</template>

<script>
export default {
  data() {
    return {
      item: "",
      todos: [
        {
          id: 1,
          title: "Item A",
          completed: false,
        },
        {
          id: 2,
          title: "Item B",
          completed: true,
        },
      ],
    };
  },
  methods: {
    addItem() {
      if (this.item === "") return;

      this.todos.push({
        id: this.todos[this.todos.length - 1].id + 1,
        title: this.item,
        completed: false,
      });
      this.item = "";
    },
    toggleItemState(itemId) {
      const item = this.todos.find((todo) => todo.id === itemId);
      item.completed = !item.completed;
    },
  },
};
</script>

<style>
input[type="text"] {
  display: block;
  width: 100%;
  font-size: 32px;
}
.completed {
  color: #ccc;
  text-decoration: line-through;
}
</style>
