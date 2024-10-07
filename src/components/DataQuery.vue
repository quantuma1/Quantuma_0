<script setup lang="ts">
import { ref } from 'vue'

const query = ref('')
const result = ref('')
const loading = ref(false)

const dataTypes = [
  { value: 'weather', label: '天气' },
  { value: 'stock', label: '股票' },
  { value: 'news', label: '新闻' },
]

const selectedType = ref(dataTypes[0].value)

const fetchData = () => {
  loading.value = true
  // 模拟API请求
  setTimeout(() => {
    result.value = `查询结果: 您查询的${selectedType.value}数据 "${query.value}" 的结果是...`
    loading.value = false
  }, 1000)
}
</script>

<template>
  <div class="query-container">
    <select v-model="selectedType">
      <option v-for="type in dataTypes" :key="type.value" :value="type.value">
        {{ type.label }}
      </option>
    </select>
    <input v-model="query" placeholder="输入查询内容" @keyup.enter="fetchData" />
    <button @click="fetchData" :disabled="loading">查询</button>
    <div v-if="loading" class="loading">加载中...</div>
    <div v-else-if="result" class="result">{{ result }}</div>
  </div>
</template>

<style scoped>
.query-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
}

select, input, button {
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ddd;
  border-radius: 4px;
}

button {
  background-color: #4CAF50;
  color: white;
  cursor: pointer;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #45a049;
}

button:disabled {
  background-color: #cccccc;
  cursor: not-allowed;
}

.loading, .result {
  margin-top: 20px;
  font-size: 18px;
}

.loading {
  color: #666;
}

.result {
  color: #2c3e50;
  font-weight: bold;
}
</style>