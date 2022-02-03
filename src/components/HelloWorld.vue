<script setup lang="ts">
import { ref } from 'vue';

defineProps<{ msg: string }>();

const count = ref(10);
</script>

<template>
  <h1>{{ msg }}</h1>

  <div style="display: flex; flex-wrap: wrap; gap: 4px">
    <div v-for="i in count" class="box">
      Application z
      <br />
      Total Spend: $93,333
    </div>
  </div>
</template>

<style scoped>
a {
  color: #42b983;
}

label {
  margin: 0 0.5em;
  font-weight: bold;
}

code {
  background-color: #eee;
  padding: 2px 4px;
  border-radius: 4px;
  color: #304455;
}

.box {
  border-radius: 8px;
  padding: 2px 4px;
  flex: 0 1 auto;
  border: green solid 1px;
}
</style>
