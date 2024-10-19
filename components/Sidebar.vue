<template>
  <div :class="{'sidebar': true, 'open': isSidebarOpen}">
    <ul>
      <li><NuxtLink to="/">Home</NuxtLink></li>
      <li><NuxtLink to="/about">About</NuxtLink></li>
      <li><NuxtLink to="/contact">Contact</NuxtLink></li>
      <li class="dropdown">
        <NuxtLink to="/program" @click.prevent="toggleDropdown('program')">Program</NuxtLink>
        <ul class="dropdown-menu" v-if="isDropdownOpen === 'program'" style="width: 245.2px;">
          <li><NuxtLink to="/program/horith">    Horith    </NuxtLink></li>
          <li><NuxtLink to="/program/shikar">Shikar</NuxtLink></li>
          <li><NuxtLink to="/program/kalpapuri">Kalpapuri</NuxtLink></li>
          <li><NuxtLink to="/program/art-factory">Art Factory</NuxtLink></li>
        </ul>
      </li>
      <li class="dropdown">
        <NuxtLink to="/project" @click.prevent="toggleDropdown('project')">Project</NuxtLink>
        <ul class="dropdown-menu" v-if="isDropdownOpen === 'project'">
          <li><NuxtLink to="/pages/project/yearly-outcome">Yearly Outcome</NuxtLink></li>
          <li><NuxtLink to="/pages/project/multidisciplinary-art-show">Multidisciplinary Art Show</NuxtLink></li>
          <li><NuxtLink to="/pages/project/art-exchange">Art Exchange</NuxtLink></li>
          <li><NuxtLink to="/pages/project/art-workshop">Art Workshop</NuxtLink></li>
          <li><NuxtLink to="/pages/project/research-program">Research Program</NuxtLink></li>
          <li><NuxtLink to="/pages/project/seminar-presentation">Seminar & Presentation</NuxtLink></li>
          <li><NuxtLink to="/project/publication">Publication</NuxtLink></li>
        </ul>
      </li>
    </ul>
    <button class="close-btn" @click="$emit('closeSidebar')">✖</button>
    <div class="overlay" v-if="isSidebarOpen" @click="$emit('closeSidebar')"></div>
  </div>
</template>

<script setup lang="ts">
import { ref, defineProps } from 'vue';

// Accept the prop
const props = defineProps<{
  isSidebarOpen: boolean;
}>();

const isDropdownOpen = ref<string | null>(null);

function toggleDropdown(type: string) {
  isDropdownOpen.value = isDropdownOpen.value === type ? null : type;
}
</script>

<style scoped>
.sidebar {
  height: 100%;
  width: 240px;
  position: fixed;
  top: 0;
  left: -250px; /* Start hidden off-screen */
  background-color: #ffffff;
  overflow-x: hidden;
  transition: 0.3s;
  padding-top: 60px;
  box-shadow: 2px 0 5px rgba(238, 237, 237, 0.1);
  z-index: 1000; /* Added z-index */
}

.sidebar.open {
  left: 0;
}

.sidebar ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.sidebar ul li {
  padding: 10px 15px;
  position: relative;
}

.sidebar ul li:hover {
  background: #e1dcdc !important;
}

.sidebar ul li a {
  color: #333;
  text-decoration: none;
}

.close-btn {
  position: absolute;
  top: 15px; /* Position the button near the top */
  right: 15px; /* Align it to the right */
  padding: 10px;
  background: none;
  border: none;
  font-size: 24px;
  color: #333;
  cursor: pointer;
  z-index: 1001; /* Ensure close button is above overlay */
  transition: color 0.3s ease;
}

.close-btn:hover {
  color: #ff0000; /* Change color on hover for visibility */
}

.overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  z-index: 999; /* Ensure overlay is above content */
}

.dropdown-menu {
  width: 245.2px;
  padding-left: 10px;
  display: block;
  list-style: none;
  padding: 0;
  margin: 0;
}

.dropdown-menu li {
  width: 245.2px;
  padding: 5px 0;
}

@media (max-width: 768px) {
  .sidebar {
    width: 60%;
  }
}
</style>
