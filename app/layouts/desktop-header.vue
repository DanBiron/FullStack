<template>
    <header class="max-w-screen bg-red-900 h-28 space-y-2 ">
        <div class="flex items-center justify-around w-full">
            <div class="flex gap-4">
                <Flame class="text-white size-8" />
                <Waves class="text-white size-8" />
                <Wind class="text-white size-8" />
                <Zap class="text-white size-8" />
                <Stone class="text-white size-8" />
            </div>
            <div class="">
                <img src="/FE_logo1_white-removebg-preview.png" alt="FE logo" class="h-16 w-64">
            </div>
            <div class=" max-w-xs">
                <UiInputGroup>
                    <UiInputGroupInput placeholder="Search..." />
                    <UiInputGroupAddon>
                        <Icon name="lucide:search" aria-label="Search" />
                    </UiInputGroupAddon>
                </UiInputGroup>
            </div>
        </div>
        <nav class="flex items-center justify-center gap-4">
            <NuxtLink to="./" class="p-2 text-medium font-bold rounded-xl hover:bg-red-950">Home</NuxtLink>
            <NuxtLink to="./about" class="p-2 text-medium font-bold rounded-xl hover:bg-red-950">About</NuxtLink>
            <NuxtLink to="./services" class="p-2 text-medium font-bold rounded-xl hover:bg-red-950">Services</NuxtLink>
            <NuxtLink to="./contact" class="p-2 text-medium font-bold rounded-xl hover:bg-red-950">Contact</NuxtLink>
            <NuxtLink to="./profile" class="p-2 text-medium font-bold rounded-xl hover:bg-red-950">Profile</NuxtLink>
        </nav>    
    </header>
    <slot />
</template>
<script setup>
import { Flame, Stone, Wind, Zap, Waves} from '@lucide/vue'

</script>
<style>
/* *{
    outline: solid red 1px;
} */
</style>
