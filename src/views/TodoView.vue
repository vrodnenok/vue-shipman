<template>
  <div class="todo-left-side">Left side</div>
  <div class="todo-main bg-gray-50 text-gray-800">
    <div class="p-8 w-3/4 mx-auto">
      <todo-add-input
        @task-added="addNewTask"
        class="block w-full rounded-md shadow-sm text-lg p-4"
      ></todo-add-input>
      <BaseCheckbox
        class="my-4 p-4 text-gray-600 text-sm font-weight-100"
        v-model="onlyPending"
      >
        <strong>Show only pending tasks</strong></BaseCheckbox
      >
    </div>
    <div class="grid grid-cols-1 gap-4 md:grid-cols-3">
      <todo-list :list="displayedTasks"></todo-list>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TodoAddInput from "@/components/todo/TodoAddInput.vue";
import TodoList from "@/components/todo/TodoList.vue";
import type { TaskItem } from "@/interfaces/TaskItem";
import TodoCheckbox from "@/components/BaseCheckbox.vue";
import BaseCheckbox from "@/components/BaseCheckbox.vue";

let idSeed = 197;

export default defineComponent({
  name: "TodoView",
  components: { BaseCheckbox, TodoList, TodoAddInput },
  data() {
    return {
      todoList: [] as TaskItem[],
      onlyPending: false,
    };
  },
  computed: {
    displayedTasks(): TaskItem[] {
      return [...this.todoList]
        .sort((a, b) => Number(b.prioritized) - Number(a.prioritized))
        .filter((task) => !this.onlyPending || !task.done);
    },
  },
  methods: {
    addNewTask(task: TaskItem) {
      console.log("About to add: ", task.description);
      task.id = Date.now() + idSeed;
      idSeed++;
      console.log("And new ID to be: ", task.id);
      this.todoList.push({
        id: task.id,
        description: task.description,
        done: false,
        prioritized: false,
      });
    },
  },
  mounted() {
    this.todoList = [
      {
        id: 1,
        description: "buy milk",
        done: true,
        prioritized: false,
      },
      {
        id: 2,
        description: "walk with the dog",
        done: false,
        prioritized: false,
      },
      {
        id: 3,
        description: "code todo list",
        done: false,
        prioritized: true,
      },
      {
        id: 4,
        description: "learn VUE",
        done: false,
        prioritized: true,
      },
      {
        id: 5,
        description: "learn CSS",
        done: false,
        prioritized: true,
      },
    ];
  },
});
</script>

<style>
.todo-left-side {
  flex: 0 0 10%;
  margin-top: 10px;
  padding: 7px;
  height: calc(100% - 30px);
  background-color: aquamarine;
}

.todo-main {
  flex: 0 0 75%;
  padding: 7px;
  margin-top: 10px;
}
</style>
