<template>
  <div class="card text-center">
    <h3 class="text-sm text-gray-500 mb-1">{{ title }}</h3>
    <p :class="['text-3xl font-bold', colorClass]">{{ value }}</p>
  </div>
</template>

<script setup lang="ts">
import { computed } from 'vue'

interface Props {
  title: string
  value: string | number
  color?: 'green' | 'red' | 'blue' | 'yellow'
}
const props = defineProps<Props>()

const colorClass = computed(() => ({
  green: 'text-green-600',
  red: 'text-red-500',
  blue: 'text-blue-500',
  yellow: 'text-yellow-400'
}[props.color ?? 'green']))
</script>
