<script setup lang="ts">
import { SpeakerWaveIcon, SpeakerXMarkIcon } from '@heroicons/vue/24/solid'
import { computed, onMounted, onUnmounted, ref } from 'vue'

const volumeLevel = ref(50)

const soundLevel = computed(() => `${volumeLevel.value}% 100%`)

const emits = defineEmits<{
  'on-volume-change': [value: number]
}>()

const addVolume = () => {
  const videoVolume =
    volumeLevel.value + 10 >= 100 ? 100 : volumeLevel.value + 10
    volumeLevel.value = videoVolume
  emits('on-volume-change', videoVolume / 100)
}
const decVolume = () => {
  const videoVolume =
    volumeLevel.value - 10 <= 0 ? 0 : volumeLevel.value - 10
    volumeLevel.value = videoVolume
  emits('on-volume-change', videoVolume / 100)
}

const adjustVolume = (event: KeyboardEvent | Event | WheelEvent) => {
  //key
  if (event instanceof KeyboardEvent) {
    if (event.code === 'ArrowUp') {
      addVolume()
      return
    }
    if (event.code === 'ArrowDown') {
      decVolume()
      return
    }
  }
  // wheel
  if (event instanceof WheelEvent) {
    if (event.deltaY < 0) {
      addVolume()
      return
    }
    if (event.deltaY > 0) {
      decVolume()
      return
    }
  }
  emits('on-volume-change', volumeLevel.value / 100)
}

onMounted(() => {
  window.addEventListener('keydown', adjustVolume)
  window.addEventListener('wheel', adjustVolume)
})
onUnmounted(() => {
  window.removeEventListener('keydown', adjustVolume)
  window.removeEventListener('wheel', adjustVolume)
})
</script>

<template>
  <div class="volume-container">
    <SpeakerWaveIcon
      v-if="volumeLevel > 0"
      @click="volumeLevel = 0"
      class="rotate-90 text-white w-[25px] mr-4"
    />
    <SpeakerXMarkIcon
      v-else
      @click="volumeLevel = 50"
      class="rotate-90 text-white w-[25px] mr-4"
    />
    <input
      type="range"
      class="volume-slider"
      min="0"
      max="100"
      @change="adjustVolume"
      @mouseleave="adjustVolume"
      v-model="volumeLevel"
    />
  </div>
</template>

<style scoped>
.volume-container {
  @apply bg-gray-600 absolute bottom-2/4 rotate-270 right-[-50px] flex p-4 rounded-lg bg-opacity-20;
}

.volume-slider {
  @apply h-[8px] w-full outline-none self-center opacity-90 cursor-pointer rounded-lg;
  background-image: linear-gradient(#f37515, #f37515);
  background-repeat: no-repeat;
  background-size: v-bind(soundLevel);
  -webkit-appearance: none;
}

.volume-slider::-webkit-slider-thumb {
  @apply h-[18px] w-[18px] self-center bg-oranje rounded-lg cursor-pointer outline-none;
  -webkit-appearance: none;
}

.volume-slider::-moz-range-thumb {
  @apply h-[18px] w-[18px] self-center bg-oranje rounded-lg cursor-pointer outline-none;
  -webkit-appearance: none;
}
</style>
