<script lang="ts" setup>
import { ref } from 'vue';
import Page from '../components/layout/Page.vue';
import Tabs from '../components/Tabs.vue'
import { tabsMock } from '../mocks/tabs';

const activeTab = ref<string>(tabsMock[0].id)
const onTabChange = (tabId: string) => {
    activeTab.value = tabId
}
</script>

<template>
    <page>
        <template #title>Home</template>
        <div>
            <tabs 
                :tabs="tabsMock" 
                :active-tab="activeTab" 
                @on-tab-change="onTabChange" 
            />
        </div>
    </page>
</template>