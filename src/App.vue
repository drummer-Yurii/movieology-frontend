<script setup lang="ts">
</script>

<template>
  <div class="flex h-screen flex-col">
    <div class="flex flex-1 overflow-hidden">
      <aside>Aside</aside>
      <main class="min-w-0 lg:flex flex-1">
        <router-view />
      </main>
    </div>
  </div>
</template>
