<script lang="ts" setup>
import { Tab } from '../types';

defineProps<{
    tabs: Tab[];
}>();
</script>

<template>
    <div>
        <nav class="flex space-x-4">
            <a v-for="{id, emoji, title} in tabs" :key="id">
                {{ emoji }}
                {{ title }}
            </a>
        </nav>
    </div>
</template>