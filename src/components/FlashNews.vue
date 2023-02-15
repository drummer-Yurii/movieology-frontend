<script setup lang="ts">
import { flashNews } from '../mocks/news';
import Stack from './Stack.vue';

const currentSlide = flashNews[0]
</script>
<template>
    <stack>
        <div class="w-full h-full bg-white rounded-2xl p-6 drop-shadow-md rotate-3">
            <div>
                <img :src="currentSlide.image" class="rounded-2xl aspect-video" alt="flash news poster">
            </div>
        </div>
    </stack>
</template>


<style>

</style>