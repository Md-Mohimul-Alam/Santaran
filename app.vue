<template>
  <div id="app">
    <Header @toggleSidebar="toggleSidebar" /> 
    <default-layout/> 
    <Footer />
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import Header from '~/components/Header.vue';
import DefaultLayout from '~/layouts/default.vue';
import Footer from './components/Footer.vue';
import 'bootstrap/dist/css/bootstrap.css';
import 'bootstrap-vue/dist/bootstrap-vue.css';

const isSidebarOpen = ref(false);

function toggleSidebar() {
  isSidebarOpen.value = !isSidebarOpen.value;
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background: #ffffff; 
  background-size: cover;
  background-repeat: no-repeat; 
  background-position: center; 
  min-height: 100vh;
  display: flex; 
  flex-direction: column; 
}

.default-layout {
  flex-grow: 1; 
  padding-bottom: 100px; 
}

h1, h2, h3, h4 {
  color: #2c3e50;
  font-weight: 600;
  letter-spacing: 1px;
  text-transform: uppercase;
  margin-bottom: 10px;
  border-bottom: 3px solid #ffe600; 
  display: inline-block;
  padding-bottom: 5px;
}

@media (max-width: 1200px) {
  #app {
    margin-top: 30px;
  }

  .default-layout {
    padding-bottom: 80px; 
  }
}

@media (max-width: 768px) {
  #app {
    margin-top: 20px;
    font-size: 90%; 
  }

  .default-layout {
    padding-bottom: 60px; 
  }
}

@media (max-width: 576px) {
  #app {
    margin-top: 10px; 
    font-size: 80%; 
  }

  .default-layout {
    padding-bottom: 40px; 
  }

  h1, h2, h3, h4 {
    font-size: 1.5rem; 
  }
}
</style>
