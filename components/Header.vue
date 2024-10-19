<template>
  <header :class="{'scrolled': isScrolled}">
    <nav>
      <ul class="desktop-nav">
        <div class="logo-container">
          <NuxtLink to="/" class="logo">
            <img src="/Santaran Logo.svg" alt="Santaran Logo" />
          </NuxtLink>
        </div>
        <li><NuxtLink to="/">Home</NuxtLink></li>
        <li><NuxtLink to="/about">About</NuxtLink></li>
        <li><NuxtLink to="/contact">Contact</NuxtLink></li>
        <li class="dropdown" @mouseenter="isDropdownOpen = true" @mouseleave="isDropdownOpen = false">
          <NuxtLink to="/program">Program</NuxtLink>
          <ul class="dropdown-menu" v-if="isDropdownOpen">
            <li><NuxtLink to="/pages/program/horith">Horith</NuxtLink></li>
            <li><NuxtLink to="/pages/program/shikar">Shikar</NuxtLink></li>
            <li><NuxtLink to="/pages/program/kalpapuri">Kalpapuri</NuxtLink></li>
            <li><NuxtLink to="/pages/program/art-factory">Art Factory</NuxtLink></li>
          </ul>
        </li>
        <li class="dropdown" @mouseenter="isProjectDropdownOpen = true" @mouseleave="isProjectDropdownOpen = false">
          <NuxtLink to="/project">Project</NuxtLink>
          <ul class="dropdown-menu" v-if="isProjectDropdownOpen">
            <li><NuxtLink to="/pages/project/yearly-outcome">Yearly Outcome</NuxtLink></li>
            <li><NuxtLink to="/pages/project/multidisciplinary-art-show">Multidisciplinary Art</NuxtLink></li>
            <li><NuxtLink to="/pages/project/art-exchange">Art Exchange</NuxtLink></li>
            <li><NuxtLink to="/pages/project/art-workshop">Art Workshop</NuxtLink></li>
            <li><NuxtLink to="/pages/project/research-program">Research Program</NuxtLink></li>
            <li><NuxtLink to="/pages/project/seminar-presentation">Seminar & Presentation</NuxtLink></li>
            <li><NuxtLink to="/pages/project/publication">Publication</NuxtLink></li>
          </ul>
        </li>
      </ul>
      <button class="hamburger" @click="toggleSidebar">☰</button>
    </nav>

    <div :class="{'sidebar': true, 'open': isSidebarOpen}">
      <button class="close-btn" @click="toggleSidebar">✖</button>
      <ul>
        <li><NuxtLink to="/">Home</NuxtLink></li>
        <li><NuxtLink to="/about">About</NuxtLink></li>
        <li><NuxtLink to="/contact">Contact</NuxtLink></li>
        <li class="dropdown" @click="toggleDropdownSidebar">
          <NuxtLink to="/program">Program</NuxtLink>
          <ul class="dropdown-menu" v-if="isDropdownOpenSidebar">
            <li><NuxtLink to="/pages/program/horith">Horith</NuxtLink></li>
            <li><NuxtLink to="/pages/program/shikar">Shikar</NuxtLink></li>
            <li><NuxtLink to="/pages/program/kalpapuri">Kalpapuri</NuxtLink></li>
            <li><NuxtLink to="/pages/program/art-factory">Art Factory</NuxtLink></li>
          </ul>
        </li>
        <li class="dropdown" @click="toggleProjectDropdownSidebar">
          <NuxtLink to="/project">Project</NuxtLink>
          <ul class="dropdown-menu" v-if="isProjectDropdownOpenSidebar">
            <li><NuxtLink to="/pages/project/yearly-outcome">Yearly Outcome</NuxtLink></li>
            <li><NuxtLink to="/pages/project/multidisciplinary-art-show">Multidisciplinary Art</NuxtLink></li>
            <li><NuxtLink to="/pages/project/art-exchange">Art Exchange</NuxtLink></li>
            <li><NuxtLink to="/pages/project/art-workshop">Art Workshop</NuxtLink></li>
            <li><NuxtLink to="/pages/project/research-program">Research Program</NuxtLink></li>
            <li><NuxtLink to="/pages/project/seminar-presentation">Seminar & Presentation</NuxtLink></li>
            <li><NuxtLink to="/pages/project/publication">Publication</NuxtLink></li>
          </ul>
        </li>
      </ul>
    </div>

    <div class="overlay" v-if="isSidebarOpen" @click="toggleSidebar"></div>
  </header>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';

const isSidebarOpen = ref(false);
const isDropdownOpen = ref(false); // For desktop dropdown
const isDropdownOpenSidebar = ref(false); // For sidebar dropdown
const isProjectDropdownOpen = ref(false); // For desktop project dropdown
const isProjectDropdownOpenSidebar = ref(false); // For sidebar project dropdown
const isScrolled = ref(false); // For scroll detection

function toggleSidebar() {
  isSidebarOpen.value = !isSidebarOpen.value; // Toggle sidebar open/close
}

function toggleDropdownSidebar() {
  isDropdownOpenSidebar.value = !isDropdownOpenSidebar.value; // Toggle program dropdown
}

function toggleProjectDropdownSidebar() {
  isProjectDropdownOpenSidebar.value = !isProjectDropdownOpenSidebar.value; // Toggle project dropdown
}

function handleScroll() {
  // Check if the window width is greater than 768px (desktop)
  if (window.innerWidth > 768) {
    isScrolled.value = window.scrollY > 0; // Set to true if scrolled down
  } else {
    isScrolled.value = false; // Reset for mobile
  }
}
// Set up event listeners
onMounted(() => {
  window.addEventListener('scroll', handleScroll);
});

// Clean up event listeners
onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
});
</script>


<style scoped>
/* Basic styles for header */
header {
  position: fixed;
  top: 0;
  width: 100%;
  left: 0;
  height: 65px;
  padding: 0 2rem;
  z-index: 1000;
  background-color: transparent; /* Light background color */
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); /* Light shadow for depth */
  transition: background-color 0.3s ease, color 0.3s ease; /* Smooth transition */
}

header.scrolled {
  background-color: #000000; /* Background color when scrolled */
  color: #ffffff !important; /* White text color when scrolled */
}

header.scrolled a {
  color: #ffffff !important; /* Ensure links are also white */
}

header.scrolled .dropdown-menu {
  background-color: #000000; /* Change dropdown menu background */
  color: #ffffff; /* Change dropdown text color */
}

header.scrolled .dropdown-menu a {
  color: #ffffff !important; /* Ensure dropdown links are white */
}

header.scrolled {
  background-color: #000000; /* Background color when scrolled */
  color: #ffffff !important; /* White text color when scrolled */
}

header.scrolled .desktop-nav li a {
  color: #ffffff !important; /* White links on desktop when scrolled */
}

@media (max-width: 768px) {
  /* Prevent changing text color on mobile when scrolled */
  header.scrolled .sidebar.open {
    background-color: #ffffff !important; /* Maintain dark color on mobile */
    color: #000000 !important;
  }
}
/* Desktop navigation styles */
.desktop-nav {
  height: 65px;
  display: flex;
  justify-content: center; /* Center items horizontally */
  align-items: center; /* Center items vertically */
  list-style-type: none;
  padding: 0;
  margin: 0;
}
.desktop-nav li {
  margin: 0 2rem; /* Adjust margin to control spacing */
  position: relative; /* Position for dropdown */
  background: transparent;
}

.desktop-nav li a {
  font-size: 16px;
  background: transparent;
  color: #000000; /* Dark text color */
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s ease; /* Add transition for hover effect */
}

.desktop-nav li a:hover {
  padding-bottom: 1px;
  background-color: transparent !important;
  border-bottom: 1px solid black;
}
.desktop-nav li a:focus {
  padding-bottom: 1px;
  background-color: transparent;
  border-bottom: 1px solid black;
}
.logo img {
  width: 150px;
  height: auto;
}

/* Dropdown styles */
.dropdown {
  position: relative;
  margin-top: 2px;
}
.dropdown:hover {
  position: relative;
  background-color: #f6efef; /* Light gray hover effect */
}

.dropdown-menu {
  margin-top: 2px;
  display: none;
  position: absolute;
  background-color: #e1e1e1; /* Light background for dropdown */
  width: 245.2px;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1); /* Light shadow for dropdown */
  z-index: 1;
}

.dropdown-menu li {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 10px 8px 8px 0px;
  list-style-type: none;
}

.dropdown-menu li:hover {
  background-color: transparent;
}

.dropdown:hover .dropdown-menu {
  display: block !important; 
}

.hamburger {
  font-size: 30px;
  background: none;
  border: none;
  cursor: pointer;
  display: none;
  color: #000000; /* Dark color for hamburger */
  transition: transform 0.3s; /* Smooth transition */
}

.hamburger:hover {
  color: #007bff; /* Change color on hover */
}


/* Sidebar styles */
.sidebar {
  height: 100%;
  width: 240px;
  position: fixed;
  top: 0;
  left: -250px; /* Start hidden off-screen */
  background-color: #ffffff !important; /* Light background for sidebar */
  color: #000000 !important;
  overflow-x: hidden;
  transition: 0.3s;
  padding-top: 60px;
  box-shadow: 2px 0 5px rgba(238, 237, 237, 0.1); /* Light shadow for sidebar */
}

.sidebar.open {
  left: 0; /* Slide in when open */
  background: #ffffff;
}

.sidebar ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.sidebar ul li {
  padding: 10px 15px;
  position: relative; /* Position for dropdown */
}
li:hover{
  background: #e1dcdc !important;
}
.sidebar ul li a {
  color: #333; /* Dark text color */
  text-decoration: none;
}

/* Close button for sidebar */
.close-btn {
  top: -20px !important;
  background: none;
  border: none;
  font-size: 30px;
  color: #333; /* Dark color for close button */
  cursor: pointer;
  position: absolute;
  top: 10px;
  right: 15px;
}

/* Overlay styles */
.overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background:transparent; /* Dark overlay */
  z-index: 999; /* Below header but above content */
}

/* Responsive styles */
@media (max-width: 768px) {
  header {
    padding-left: 15px;
    
    background-color: transparent; /* Make header transparent on mobile */
    box-shadow: none; /* Remove shadow for transparency effect */
  }

  .desktop-nav {
    display: none; /* Hide desktop nav on small screens */
  }
  
  .hamburger {
    display: block; /* Show hamburger on small screens */
  }

  .sidebar {
    width: 60%; /* Adjust sidebar width on mobile */
    background: #ffffff;
  }
  .sidebar ul li:hover{
    background: #e1dcdc !important;
  }
  .hamburger{
    padding-left: -10px;
    padding-top: 8px;
  }
}
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
  padding-top: 60px;
  background: none;
  border: none;
  font-size: 24px;
  color: #333;
  cursor: pointer;
  z-index: 1001; /* Ensure close button is above overlay */
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
  padding-left: 10px;
  display: block;
  list-style: none;
  padding: 0;
  margin: 0;
}

.dropdown-menu li {
  padding: 5px 0;
}

@media (max-width: 768px) {
  .sidebar {
    width: 60%;
  }
}
</style>
