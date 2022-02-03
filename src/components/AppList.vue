<script setup lang="ts">
import { ref } from 'vue';

defineProps<{ msg: string; items: any[] }>();
</script>

<template>
  <h1>{{ msg }}</h1>

  <div style="display: flex; flex-wrap: wrap; gap: 5px">
    <div v-for="{ spend, name, id } in items" :key="id" class="box">
      <b>{{ name }}</b>
      <br />
      <br />
      Total Spend: ${{ spend }}
    </div>
  </div>
</template>

<style scoped>
.box {
  border-radius: 8px;
  padding: 30px 15px;
  flex: 0 1 auto;
  min-width: 150px;
  border: green solid 1px;
}
</style>
