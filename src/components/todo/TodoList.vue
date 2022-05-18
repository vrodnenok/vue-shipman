<template>
  <TodoListItem
    v-for="item in list"
    :key="item.id"
    v-model:done="item.done"
    v-model:prioritized="item.prioritized"
    :task="item"
  ></TodoListItem>
</template>

<script lang="ts">
import type { TaskItem } from "@/interfaces/TaskItem";
import TodoListItem from "@/components/todo/TodoListItem.vue";

export default {
  name: "TodoList",
  components: { TodoListItem },
  props: {
    list: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped></style>
