<script setup lang="ts">
import { computed, ref } from 'vue'

const props = defineProps<{
  isActive: boolean
  videoDuration: number
  currentVideoPosition: number
}>()

const timeBar = ref<number>(0)

const emits = defineEmits<{ 'on-time-change': [value: number] }>()

const updateTimeBar = (event: Event) => {
  const currentTarget = event.target as HTMLInputElement
  timeBar.value = +currentTarget.value
  emits('on-time-change', timeBar.value)
}

const calculateTime = (duration: number) => {
  const seconds = Math.floor(duration % 60)
  const minutes = Math.floor(duration / 60)
  const computedSeconds = seconds >= 10 ? seconds : `0 ${seconds}`
  return `${minutes}:${computedSeconds}`
}

const currentTime = computed(() => calculateTime(props.currentVideoPosition))
const timeTotal = computed(() => calculateTime(props.videoDuration))
</script>

<template>
  <div class="controls" v-bind="$attrs">
    <time>{{ currentTime }}</time>
    <input
      type="range"
      class="time-track"
      :min="0"
      step="10"
      :max="videoDuration"
      :value="currentVideoPosition"
      @change="updateTimeBar"
    />
    <time>{{ timeTotal }}</time>
  </div>
</template>

<style scoped></style>
