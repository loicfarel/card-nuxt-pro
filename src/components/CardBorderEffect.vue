<script setup lang="ts">
import { Icon } from '@iconify/vue'
import CardContainer from './CardContainer.vue'

defineProps<{
  label: string
  description: string
  to?: string
  icon?: string
}>()
</script>

<template>
  <CardContainer>
    <div
      class="flex flex-col flex-1 px-4 py-5 gap-x-8 gap-y-4 rounded-xl sm:p-6 dark:bg-gray-900/50"
    >
      <div>
        <a v-if="to" :href="to" class="focus:outline-none" tabindex="-1"
          ><span class="absolute inset-0"></span
        ></a>
        <div v-if="icon" class="mb-2 pointer-events-none">
          <Icon :icon="icon" class="flex-shrink-0 text-gray-900 size-8 dark:text-white" />
        </div>
        <p class="text-base font-bold text-gray-900 truncate dark:text-white">
          {{ label }}
        </p>
        <div class="text-[15px] text-gray-500 dark:text-gray-400 mt-1">
          {{ description }}
        </div>
      </div>
    </div>
  </CardContainer>
</template>

<style scoped></style>
