<template>
  <nav class="navbar">
    <div class="navbar-brand">
      <span class="brand-title">{{ titulo }}</span>
    </div>
    <ul class="navbar-links">
      <li><a href="#inicio">Inicio</a></li>
      <li><a href="#arcs">Tipos de Arc</a></li>
      <li><a href="#info">Acerca del juego</a></li>
    </ul>
  </nav>
</template>

<script setup>
defineProps({
  titulo: {
    type: String,
    required: true
  }
})
</script>

<style scoped>
.navbar {
  background-color: #1a1a2e;
  color: #e0e0e0;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 12px 32px;
  position: sticky;
  top: 0;
  z-index: 100;
  border-bottom: 2px solid #e63946;
}

.brand-title {
  font-size: 1.3rem;
  font-weight: bold;
  color: #e63946;
  letter-spacing: 1px;
}

.navbar-links {
  list-style: none;
  display: flex;
  gap: 24px;
  margin: 0;
  padding: 0;
}

.navbar-links a {
  color: #e0e0e0;
  text-decoration: none;
  font-size: 0.95rem;
  transition: color 0.2s;
}

.navbar-links a:hover {
  color: #e63946;
}
</style>
