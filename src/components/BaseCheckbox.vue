<template>
  <div class="flex items-center">
    <input
      type="checkbox"
      class="h-4 w-4 text-indigo-600 border-gray-300 rounded mr-2"
      :checked="modelValue"
      @change="onChange"
    />
    <label><slot>Checkbox</slot></label>
  </div>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "BaseCheckbox",
  emits: ["update:modelValue"],
  props: {
    modelValue: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    onChange() {
      this.$emit("update:modelValue", !this.modelValue);
    },
  },
});
</script>

<style scoped></style>
