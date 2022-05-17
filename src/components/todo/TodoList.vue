<template>
  <div>list of todo items</div>
  <div v-for="item in list" :key="item.id" >{{item.description}}</div>
</template>

<script lang="ts">
import type {TaskItem} from "@/interfaces/Task";

export default {
  name: "TodoList",
  props: {
    list: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>

</style>