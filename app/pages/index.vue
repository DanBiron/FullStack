<template>
    <main class="bg-neutral-100 min-h-screen max-w-screen">
        <section class="flex flex-col items-center gap-5">
            <UiCarousel
            class="relative w-full max-w-3/4"
            :plugins="[plugin]"
            @mouseenter="plugin.stop"
            @mouseleave="[plugin.reset(), plugin.play(), console.log('Running')]"
            >
            <UiCarouselContent>
                <UiCarouselItem v-for="(_, index) in 5" :key="index" grab-cursor>
                    <div class="p-1">
                        <UiCard>
                            <UiCardContent class="flex items-center justify-center p-6 aspect-4/2">
                                <span class="text-4xl font-semibold">{{ index + 1 }}</span>
                            </UiCardContent>
                        </UiCard>
                    </div>
                </UiCarouselItem>
            </UiCarouselContent>
            <UiCarouselPrevious class="bg-red-600!" />
            <UiCarouselNext class="bg-red-600!" />
            </UiCarousel>
        </section>
        <div class="p-4">
            <strong class="text-black block text-center">EVENTS</strong>
        </div>
        <div class="grid grid-cols-4 gap-4 p-4">
            <div class="col-span-3 border rounded-2xl bg-accent h-44">

            </div>
            <div class="col-span-1 border rounded-2xl bg-accent">

            </div>
        </div>
    </main>
</template>

<script setup lang="ts">
definePageMeta({
    layout: 'desktop-header'
})
import Autoplay from "embla-carousel-autoplay";

  const plugin = Autoplay({
    delay: 2000,
    stopOnMouseEnter: true,
    stopOnInteraction: false,
  });
</script>

<style>
/* *{
    outline: 1px solid red;
} */
</style>