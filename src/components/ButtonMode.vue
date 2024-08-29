<script setup lang="ts">
import {useDark, useToggle } from '@vueuse/core'
import { Icon } from '@iconify/vue'

const isDark = useDark()
const toggleDark = useToggle(isDark)
</script>

<template>
  <button
    @click="toggleDark()"
    type="button"
    class="flex-shrink-0 rounded-md gap-x-1.5 p-1.5 text-gray-700 dark:text-gray-200 hover:text-gray-900 dark:hover:text-white hover:bg-gray-50 dark:hover:bg-gray-800 inline-flex items-center"
  >
    <Icon v-if="isDark" icon="ph:moon-duotone" class="size-6" />
    <Icon v-else icon="ph:sun-duotone" class="size-6" /> 
  </button>
</template>
