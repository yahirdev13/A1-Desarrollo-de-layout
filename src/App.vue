

<template>
  <div id="app">
    <header>
      <!-- Navbar -->
      <nav>
        <div class="navbar">
          <div class="logo">Logo</div>
          <div class="navbar-links">
            <a href="#">Inicio</a>
            <div class="dropdown">
              <a href="#">Lang</a>
              <div class="dropdown-content">
                <a href="#">Español</a>
                <a href="#">English</a>
              </div>
            </div>
            <div class="dropdown">
              <a href="#">User</a>
              <div class="dropdown-content">
                <a href="#">Account</a>
                <a href="#">Settings</a>
              </div>
            </div>
          </div>
        </div>
      </nav>
    </header>

    <!-- Sidebar -->
    <aside v-show="sidebarVisible" class="sidebar">
      <div class="sidebar-content">
        <p>
          Aqui va el contenido de la sidebar
        </p>
        
      </div>
    </aside>

    <!-- Contenido principal de tu página -->
    <main :style="{ marginLeft: sidebarVisible ? '275px' : '0' }">
      <router-view>
        <h1 >Contenido principal</h1>
        <p >Aqui se supone que va el contenido de la pagina que ira cambiando dependiendo de la vista que se tiene</p>
      </router-view>
    </main>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const sidebarVisible = ref(true);
</script>

<style scoped>
body {
  margin: 0;
  padding: 0;
  font-family: Arial, sans-serif;
}

header {
  background-color: #1eb8ff;
  position: relative;
  color: white;
  padding: 15px;
  z-index: 2;
}

.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  font-size: 1.5em;
}

.navbar-links {
  display: flex;
  gap: 20px;
}

.navbar-links a {
  color: white;
  text-decoration: none;
}

.dropdown {
  position: relative;
}

.dropdown-content {
  display: none;
  position: absolute;
  background-color: #333;
  min-width: 160px;
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
  z-index: 1;
}

.dropdown:hover .dropdown-content {
  display: block;
}

.sidebar {
  background-color: #222;
  color: white;
  height: 100vh;
  width: 250px;
  position: fixed;
  top: 0;
  left: 0;
  transition: margin 0.5s;
  z-index: 1;
}

.sidebar-content {
  margin-top: 75px;
  padding: 15px;
}

main {
  margin-top: 60px;
  transition: margin 0.5s;
}
</style>
