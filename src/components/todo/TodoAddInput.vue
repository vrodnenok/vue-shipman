<template>
  <p>Here goes form to add new todo task</p>
  <form @submit.prevent>
    <input
      type="text"
      placeholder="Input task description here"
      v-model="task.description"
      @keyup.enter="addTask"
    />
  </form>
</template>

<script lang="ts">
import type { TaskItem } from "@/interfaces/TaskItem";
import { defineComponent } from "vue";

export default defineComponent({
  name: "TodoAddInput",
  data() {
    return {
      task: {
        id: 0,
        description: "",
        done: false,
        prioritized: false,
      },
    };
  },
  emits: ["task-added"],
  methods: {
    addTask() {
      console.log(this.task);
      this.$emit("task-added", this.task);
      this.task.description = "";
    },
  },
});
</script>

<style scoped></style>
