<script lang="ts" setup>
import { Tab } from '../types';

defineProps<{
    tabs: Tab[];
}>();
</script>

<template>
    <div>
        <nav class="flex space-x-4">
            <a 
                class="bg-movie-black-200 rounded-lg px-5 py-2 text-white drop-shadow-sm hover:bg-oranje cursor-pointer" 
                v-for="{ id, emoji, title } in tabs" 
                :key="id"
            >
                {{ emoji }}
                {{ title }}
            </a>
        </nav>
    </div>
</template>