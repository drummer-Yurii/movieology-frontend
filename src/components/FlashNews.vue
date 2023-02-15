<script setup lang="ts">
import { ArrowRightIcon } from '@heroicons/vue/24/solid';
import { flashNews } from '../mocks/news';
import Stack from './Stack.vue';

const currentSlide = flashNews[0]
</script>
<template>
    <stack>
        <div class="w-full bg-white rounded-2xl p-6 drop-shadow-md rotate-3">
            <div class="news-top">
                <img :src="currentSlide.image" class="rounded-2xl" alt="flash news poster">
                <h2 class="text-oranje mt-2 font-bold text-m">🔥Hot News</h2>
                <p class="mt-2 font-bold">{{ currentSlide.text }}</p>
            </div>
            <div class="news-footer mt-4 flex">
                <p class="text-gray-400 w-full">
                    {{ currentSlide.date }}
                </p>
                <p class="text-gray-900 flex">1/5 <ArrowRightIcon class="w-6 ml-2" /></p>
            </div>
        </div>
    </stack>
</template>


<style>

</style>