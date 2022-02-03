<script setup>
import { ref } from 'vue';
import TreeItem from './TreeItem.vue';

const props = defineProps({
  treeData: Object,
});
</script>

<template>
  <h3>Navigation</h3>
  <ul>
    <TreeItem
      v-for="item in treeData.children"
      :model="item"
      class="item"
    ></TreeItem>
  </ul>
</template>

<style>
.item {
  cursor: pointer;
  line-height: 1.5;
}
.bold {
  font-weight: bold;
}
</style>
