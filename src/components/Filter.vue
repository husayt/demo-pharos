<script setup lang="ts">
import { ref, onUnmounted } from 'vue';

defineProps<{ min?: number; max?: number; modelValue: number }>();
defineEmits(['update:modelValue']);
</script>

<template>
  <div>
    <h3>Filters</h3>
    <label for="filter-range" style="text-align: left"
      ><div>Spending:</div></label
    >
    <input
      type="range"
      id="filter-range"
      name="filter-range"
      :value="modelValue"
      :min="min"
      :max="max"
      @input="$emit('update:modelValue', +$event.target.value)"
    />
    <div style="display: flex; justify-content: space-between">
      <span>${{ min }}</span> <span>${{ max }}</span>
    </div>
  </div>
</template>

<style>
.elapsed-container {
  width: 300px;
}

.elapsed-bar {
  background-color: red;
  height: 10px;
}
</style>
