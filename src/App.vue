<script setup lang="ts">
import { onMounted, ref, computed } from 'vue';
import AppList from './components/AppList.vue';
import TreeView from './components/TreeView.vue';
import Filter from './components/Filter.vue';

const data = ref([]),
  treeData = ref([]),
  curFilter = ref(100),
  min = ref(0),
  max = ref(0);

onMounted(async () => {
  data.value = await (await fetch('data.json')).json();
  const root = {
    name: 'root',
    children: [],
  };
  function findItem(item, parent, level) {
    let node = parent.children.find((x) => x.name === item[level]);
    if (!node) {
      node = { name: item[level], children: [], level };
      parent.children.push(node);
    }
    return node;
  }

  let minS = data.value[0].spend,
    maxS = data.value[0].spend;
  for (let item of data.value) {
    let node1 = findItem(item, root, 'BCAP1');
    let node2 = findItem(item, node1, 'BCAP2');
    let node3 = findItem(item, node2, 'BCAP3');
    node3.children.push(item);
    if (item.spend > maxS) maxS = item.spend;
    if (item.spend < minS) minS = item.spend;
  }
  min.value = minS;
  max.value = maxS;
  treeData.value = root;
});

const filteredData = computed(() => {});
</script>

<template>
  <div class="flex-row" style="gap: 0.5rem">
    <div class="flex-col" style="justify-content: flex-start">
      <TreeView class="tree-container" :treeData="treeData" />
      {{ curFilter }}
      <Filter v-model="curFilter" :min="min" :max="max" />
    </div>
    <div class="flex-col right-container">
      <AppList :items="data" msg="Pharos Systems" />
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
