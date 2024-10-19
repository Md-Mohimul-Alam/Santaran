<template>
  <div class="default-layout">
    <Sidebar :isSidebarOpen="isSidebarOpen" @closeSidebar="toggleSidebar" />
    <div class="content">
      <NuxtPage />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import Sidebar from '~/components/Sidebar.vue';

const isSidebarOpen = ref(false);

function toggleSidebar() {
  isSidebarOpen.value = !isSidebarOpen.value;
}
</script>

<style scoped>
.default-layout {
  display: flex;
  height: 100vh;
  width: 100vw;
  background-color: #ffffff;
  background-size: cover;
  background-position: center;
}

Sidebar {
  width: 250px; 
  flex-shrink: 0; 
}

.content {
  top: 0;
  flex: 1;
  max-height: 100vh;
  padding: 0;
}

@media (max-width: 768px) {
  .content {
    padding: 0px;
    margin-left: -4px;
  }
}

@media (max-width: 576px) {
  .content {
    padding: 0px;
    margin-left: 0;
  }
}
</style>
