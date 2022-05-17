<template>
  <div
  class="todo-left-side">Right side</div>
  <div class="todo-main">
    <p> test main block</p>
    <todo-add-input @task-added="addNewTask"></todo-add-input>
    <todo-list :list="todoList" ></todo-list>
    <pre>{{todoList}}</pre>
  </div>
</template>

<script lang="ts">
import {defineComponent} from "vue";
import TodoAddInput from "@/components/todo/TodoAddInput.vue";
import TodoList from "@/components/todo/TodoList.vue";
import type {TaskItem} from "@/interfaces/Task";

let idSeed = 197;

export default defineComponent({
  name: "TodoView",
  components: {TodoList, TodoAddInput},
  data(){
    return{
      todoList: [] as TaskItem[]
    }
  },
  methods:{
    addNewTask(task: TaskItem){
      console.log("About to add: ", task.description)
      task.id=Date.now()+idSeed;
      idSeed++;
      console.log("And new ID to be: ", task.id)
      this.todoList.push({
        id: task.id,
        description: task.description,
        done: false,
        prioritized: false
      });
    }
  },
  mounted(){
    this.todoList=[
      {
        id: 1,
        description: "buy milk",
        done: true,
        prioritized: false
      },
      {
        id: 2,
        description: "walk with the dog",
        done: false,
        prioritized: false
      },
      {
        id: 3,
        description: "code todo list",
        done: false,
        prioritized: true
      },
      {
        id: 4,
        description: "learn VUE",
        done: false,
        prioritized: true
      },
      {
        id: 5,
        description: "learn CSS",
        done: false,
        prioritized: true
      }
    ]
  },
})
</script>

<style>
.todo-left-side{
  flex: 0 0 10%;
  margin-top: 10px;
  padding: 7px;
  height: calc(100% - 30px);
  background-color: aquamarine;
}

.todo-main{
  flex: 0 0 75%;
  padding: 7px;
  margin-top: 10px;
  background-color: beige;
}
</style>