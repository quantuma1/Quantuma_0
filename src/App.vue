<script setup lang="ts">
import { ref } from 'vue'
import DataQuery from './components/DataQuery.vue'

const title = ref('数据查询系统')
</script>

<template>
  <div class="container">
    <h1>{{ title }}</h1>
    <DataQuery />
  </div>
</template>

<style scoped>
.container {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
  text-align: center;
}

h1 {
  color: #2c3e50;
  margin-bottom: 20px;
}
</style>