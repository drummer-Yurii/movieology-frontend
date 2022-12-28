<script lang="ts" setup>
import Page from '../components/layout/Page.vue';
import Tabs from '../components/Tabs.vue'
import { tabs } from '../mocks/tabs';
</script>

<template>
    <page>
        <template #title>Home</template>
        <div>
            <tabs :tabs="tabs" />
        </div>
    </page>
</template>