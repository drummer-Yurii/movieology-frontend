<script setup lang="ts">
import { ArrowRightIcon, ArrowLeftIcon } from '@heroicons/vue/24/solid';
import { computed, ref } from 'vue';
import { flashNews } from '../mocks/news';
import Stack from './Stack.vue';

interface FlashNews {
    id: number;
    rotate: number;
    image: string;
    text: string;
    date: string;
}

const currentSlideIndex = ref<number>(0)
const currentSlide = computed(() => flashNews[currentSlideIndex.value])
const isLastSlide = computed(() => currentSlideIndex.value >= flashNews.length - 1)

const nextSlide = () => {
    if (isLastSlide.value) {
        return;
    }
    currentSlideIndex.value++
}

const prevSlide = () => {
    if (currentSlideIndex.value === 0) {
        return;
    }
    currentSlideIndex.value--
}
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
                <p class="text-gray-900 flex">
                    <ArrowLeftIcon v-if="currentSlideIndex > 0" class="w-6 mr-2" @click="prevSlide" />
                    {{ currentSlideIndex + 1 }}/{{ flashNews.length }} 
                    <ArrowRightIcon v-if="!isLastSlide" class="w-6 ml-2" @click="nextSlide" />
                    <div v-else class="w-6 ml-2"></div>
                </p>
            </div>
        </div>
    </stack>
</template>


<style>

</style>