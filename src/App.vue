<template>
  <div id="app">
    <aside class="sidebar" :class="{ 'sidebar-collapsed': !isSidebarOpen }">
      <button class="toggle-button" @click="toggleSidebar">
        {{ isSidebarOpen ? 'Close' : 'Open' }}
      </button>
      <nav v-if="isSidebarOpen">
        <ul>
          <li><router-link to="/">Home</router-link></li>
          <li><router-link to="/about">About</router-link></li>
          <li><router-link to="/dashboard">Dashboard</router-link></li>
        </ul>
      </nav>
    </aside>
    <main class="content">
      <router-view></router-view>
    </main>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const isSidebarOpen = ref(true); // Initial state of the sidebar

const toggleSidebar = () => {
  isSidebarOpen.value = !isSidebarOpen.value;
};
</script>

<style scoped>
#app {
  display: flex;
}

.sidebar {
  width: 200px;
  background-color: #f0f0f0;
  padding: 20px;
  transition: width 0.3s ease; /* Add transition for smooth animation */
}

.sidebar-collapsed {
  width: 60px; /* Adjust as needed for the collapsed state */
  /* Hide the content (e.g., links) when collapsed */
}

.toggle-button {
  margin-bottom: 10px;
}

/* Hide links when the sidebar is collapsed */
.sidebar-collapsed nav {
  display: none;
}

.sidebar ul {
  list-style: none;
  padding: 0;
}

.sidebar li {
  margin-bottom: 10px;
}

.sidebar a {
  text-decoration: none;
  color: #333;
  display: block;
  padding: 5px;
}

.sidebar a.router-link-active {
  background-color: #ddd;
  font-weight: bold;
}

.content {
  flex-grow: 1;
  padding: 20px;
}
</style>