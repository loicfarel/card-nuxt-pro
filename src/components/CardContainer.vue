<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const cover = ref<HTMLElement | null>(null),
  x = ref(-350),
  y = ref(-350)

function mouseMoveGradient(e: MouseEvent) {
  if (cover.value) {
    const rect = cover.value.getBoundingClientRect()
    const diffX = e.clientX - rect.x
    const diffY = e.clientY - rect.y
    x.value = diffX
    y.value = diffY
  }
}

onMounted(() => {
  document.addEventListener('mousemove', mouseMoveGradient, false)
})

onUnmounted(() => {
  document.removeEventListener('mousemove', mouseMoveGradient, false)
})
</script>
<template>
  <div
    ref="cover"
    class="cover relative isolate rounded-xl background-gradient ring-1 ring-gray-200 dark:ring-gray-800 before:hidden before:lg:block before:absolute before:-inset-[2px] before:h-[calc(100%+4px)] before:w-[calc(100%+4px)] before:z-[-1] before:rounded-[13px] flex-1 flex flex-col shadow transition-shadow duration-200"
    :style="{ '--x': x + 'px', '--y': y + 'px' }"
  >
    <div
      class="flex-1 flex flex-col overflow-hidden rounded-xl divide-y divide-gray-200 dark:divide-gray-800 bg-white dark:bg-gray-900 hover:bg-opacity-90 dark:hover:bg-opacity-90 transition-[background-opacity] dark:bg-gradient-to-b from-gray-700/50 to-gray-900/50"
    >
      <slot />
    </div>
  </div>
</template>

<style scoped>
.cover:before {
  background: radial-gradient(250px circle at var(--x) var(--y), #40c371 0, transparent 100%);
}
</style>
