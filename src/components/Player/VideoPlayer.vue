<script setup lang="ts">

</script>

<template>
    <div class="player" ref="player">
        <video 
            class="video-screen" 
            src="../../assets/video.mp4" 
            controls
            preload="auto"
            ref="video"
            allowfullscreen
            type="video/mp4"
        />
        <time-control />
        <volume-control />
    </div>
</template>

<style>
.player {
    @apply w-full rounded-lg aspect-video relative object-cover cursor-pointer; 
}

.video-screen {
    @apply aspect-video shadow-sm block w-full h-full cursor-pointer bg-movie-black-200;
}

::-webkit-media-controls {
    display: none;
}
</style>