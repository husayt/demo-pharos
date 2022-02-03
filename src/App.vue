<script setup lang="ts">
import { onMounted } from 'vue';
import HelloWorld from './components/HelloWorld.vue';
import TreeView from './components/TreeView.vue';
import Filter from './components/Filter.vue';

onMounted(() => {
  console.log('hello');
});
</script>

<template>
  <div class="flex-row" style="gap: 0.5rem">
    <div class="flex-col" style="justify-content: space-between">
      <TreeView class="tree-container" />
      <Filter />
    </div>
    <div class="flex-col right-container">
      <img alt="Vue logo" style="height: 50px" src="/logo.png" />
      <HelloWorld msg="Hello Vue 3 + TypeScript + Vite" />
    </div>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h3 {
  text-align: left;
}

.flex-row {
  display: flex;
}
.flex-col {
  display: flex;
  flex-direction: column;
}
.right-container {
  border-left: 1px solid black;
  padding-left: 5px;
}

.tree-container {
  justify-self: stretch;
  flex: 1 1 auto;
  border-bottom: 1px solid black;
}
</style>
