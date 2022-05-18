<template>
  <div
    class="bg-white shadow-sm rounded-md text-gray-700 text-xs md:text-sm p-4"
    :class="{ 'opacity-25 line-through': task.done }"
  >
    <div>
      <strong>{{ task.description }}</strong>
    </div>
    <div class="py-4 bg-white">
      <BaseCheckbox
        class="mb-2"
        :model-value="prioritized"
        @update:model-value="$emit('update:prioritized', $event)"
        >Is high priority?</BaseCheckbox
      >
      <BaseCheckbox
        :model-value="done"
        @update:model-value="$emit('update:done', $event)"
        >Is done?</BaseCheckbox
      >
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import BaseCheckbox from "@/components/BaseCheckbox.vue";
import type { TaskItem } from "@/interfaces/TaskItem";

export default defineComponent({
  name: "TodoListItem",
  components: { BaseCheckbox },
  props: {
    task: {
      type: Object,
      required: true,
    },
    done: Boolean,
    prioritized: Boolean,
  },
  emits: ["update:done", "update:prioritized"],
});
</script>

<style scoped></style>
