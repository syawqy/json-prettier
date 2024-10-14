<script setup lang="ts">
import { ref } from 'vue';

const originalJson = ref('');
const formattedJson = ref('');

const formatJson = () => {
  try {
    const parsed = JSON.parse(originalJson.value);
    formattedJson.value = JSON.stringify(parsed, null, 2);
  } catch (error) {
    formattedJson.value = 'Invalid JSON';
  }
};
</script>

<template>
  <div class="container mx-auto px-4 py-8 max-w-6xl">
    <h1 class="text-4xl font-bold text-center mb-8 text-indigo-600">JSON Prettier</h1>
    <div class="mb-6 text-center">
      <button @click="formatJson" class="bg-indigo-600 text-white px-6 py-2 rounded-lg hover:bg-indigo-700 transition duration-300 ease-in-out transform hover:scale-105 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-opacity-50">
        Format JSON
      </button>
    </div>
    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
      <div class="bg-white rounded-lg shadow-md p-6">
        <h2 class="text-xl font-semibold mb-4 text-gray-700">Original JSON</h2>
        <textarea 
          v-model="originalJson" 
          placeholder="Enter your JSON here" 
          class="w-full h-96 p-3 border border-gray-300 rounded-md focus:ring-2 focus:ring-indigo-500 focus:border-indigo-500 resize-none font-mono text-sm"
        ></textarea>
      </div>
      <div class="bg-white rounded-lg shadow-md p-6">
        <h2 class="text-xl font-semibold mb-4 text-gray-700">Formatted JSON</h2>
        <textarea 
          v-model="formattedJson" 
          readonly 
          class="w-full h-96 p-3 bg-gray-50 border border-gray-300 rounded-md font-mono text-sm"
        ></textarea>
      </div>
    </div>
  </div>
</template>