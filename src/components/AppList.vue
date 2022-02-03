<script setup lang="ts">
import { ref } from 'vue';

defineProps<{ msg: string; items: any[] }>();
</script>

<template>
  <h1>{{ msg }}</h1>

  <div style="display: flex; flex-wrap: wrap; gap: 4px">
    <div v-for="{ spend, name } in items" class="box">
      {{ name }}
      <br />
      Total Spend: ${{ spend }}
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
  padding: 10px 5px;
  flex: 0 1 auto;
  border: green solid 1px;
}
</style>
