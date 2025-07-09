<template>
  <aside class="sidebar">
    <nav>
      <ul>
        <li v-for="item in menuItems" :key="item.name">
          <router-link :to="item.path">{{ item.name }}</router-link>
        </li>
      </ul>
    </nav>
  </aside>
</template>

<script setup lang="ts">
interface MenuItem {
  name: string;
  path: string;
}

const menuItems: MenuItem[] = [
  { name: 'Home', path: '/' },
  { name: 'About', path: '/about' },
  { name: 'Contact', path: '/contact' },
];
</script>

<style scoped>
.sidebar {
  width: 200px;
  background-color: #f0f0f0;
  padding: 20px;
  height: 100vh; /* Full height */
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
  font-weight: bold;
}

.sidebar a.router-link-active {
  color: #007bff;
}
</style>