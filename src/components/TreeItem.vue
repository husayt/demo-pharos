<script setup>
import { ref, computed } from 'vue';

const props = defineProps({
  model: Object,
});

const isOpen = ref(false);
const isFolder = computed(() => {
  return props.model.children && props.model.children.length;
});
</script>

<template>
  <li class="list-item">
    <div :class="{ bold: isFolder }" @click="isOpen = !isOpen">
      <span v-if="isFolder">{{ isOpen ? '▲' : '▼' }}</span>
      {{ model.name }}
    </div>
    <ul v-show="isOpen" v-if="isFolder">
      <TreeItem class="item" v-for="model in model.children" :model="model">
      </TreeItem>
    </ul>
  </li>
</template>

<style scoped>
.list-item {
  margin-left: -20px;
  list-style-type: none;
  text-align: left;
  white-space: nowrap;
}
</style>
