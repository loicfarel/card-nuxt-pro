<script setup lang="ts">
import { ref } from 'vue'
import { webDevelopmentCards } from '@/cards'
import CardBorderEffect from '@/components/CardBorderEffect.vue'
import ButtonMode from '@/components/ButtonMode.vue'

const cards = ref(webDevelopmentCards)
</script>

<template>
  <main
    class="w-screen min-h-screen overflow-x-hidden dark:bg-gradient-to-b from-gray-900 to-gray-950"
  >
    <header class="flex justify-end px-8 py-4">
      <ButtonMode />
    </header>
    <section class="py-8 sm:py-16">
      <div class="flex flex-col gap-16 px-4 mx-auto sm:px-6 lg:px-8 max-w-7xl sm:gap-y-20">
        <div class="flex flex-col items-center text-center">
          <h2
            class="text-3xl font-bold tracking-tight text-gray-900 dark:text-white sm:text-4xl lg:text-5xl"
          >
            <span>Cards with<br /><span class="text-primary">border hover effect.</span></span>
          </h2>
        </div>
        <div class="grid grid-cols-1 gap-8 sm:grid-cols-2 xl:grid-cols-4">
          <CardBorderEffect
            v-for="(card, index) in cards"
            :key="index"
            :label="card.label"
            :description="card.description"
            :icon="card.icon"
            :to="card.to"
          />
        </div>
      </div>
    </section>
  </main>
</template>

<style scoped>
.text-primary {
  color: rgb(0, 220, 130);
}
</style>
