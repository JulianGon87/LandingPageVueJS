<template>
  <NavBar :titulo="sitioTitulo" />

  <section id="inicio" class="hero">
    <h1>Arc Raiders</h1>
    <p class="hero-sub">
      En un mundo post-invasión, los Raiders luchan por sobrevivir contra los <strong>ARCS</strong>,
      máquinas autónomas de origen desconocido que controlan la superficie.
    </p>
  </section>

  <section id="arcs" class="seccion-arcs">
    <h2>Tipos de Unidades Arc</h2>
    <p class="seccion-descripcion">
      Conoce las amenazas que encontrarás en cada incursión. Total de unidades catalogadas:
      <strong>{{ totalArcs }}</strong>
    </p>

    <div class="grid-tarjetas">
      <ArcCard
        v-for="arc in arcs"
        :key="arc.id"
        :arc="arc"
      />
    </div>
  </section>


  <section id="info" class="seccion-info">
    <h2>Acerca del juego</h2>
    <p>
      <strong>Arc Raiders</strong> es un juego de acción cooperativo desarrollado por Embark Studios.
      Los jugadores forman equipos de Raiders para enfrentarse a oleadas de unidades automatizadas
      llamadas "Arcs" y extraer recursos de zonas de alto riesgo.
    </p>
  </section>

  <footer class="footer">
    <p>Ejercicio Práctico · Módulo 6 Lección 1 · Vue.js</p>
  </footer>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import NavBar from './components/NavBar.vue'
import ArcCard from './components/ArcCard.vue'
import arcsData from './data/arcs.json'

const arcs = ref([])
const sitioTitulo = ref('Arc Raiders — Guía de Unidades')
const totalArcs = ref(0)

onMounted(() => {
  arcs.value = arcsData
  totalArcs.value = arcsData.length
})
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  background-color: #0d0d1a;
  color: #e0e0e0;
  font-family: 'Segoe UI', Arial, sans-serif;
  line-height: 1.6;
}

.hero {
  text-align: center;
  padding: 60px 20px 40px;
  background-color: #11112a;
  border-bottom: 1px solid #2a2a4a;
}

.hero h1 {
  font-size: 2.4rem;
  color: #e63946;
  margin-bottom: 14px;
  letter-spacing: 2px;
}

.hero-sub {
  max-width: 620px;
  margin: 0 auto;
  color: #b0b0c0;
  font-size: 1rem;
}

.seccion-arcs {
  padding: 44px 40px;
}

.seccion-arcs h2,
.seccion-info h2 {
  font-size: 1.5rem;
  color: #c9c9e0;
  margin-bottom: 8px;
  border-left: 4px solid #e63946;
  padding-left: 12px;
}

.seccion-descripcion {
  color: #888;
  font-size: 0.9rem;
  margin-bottom: 28px;
}

.grid-tarjetas {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 20px;
}

.seccion-info {
  padding: 40px 40px;
  background-color: #11112a;
  border-top: 1px solid #2a2a4a;
}

.seccion-info p {
  margin-top: 14px;
  color: #b0b0c0;
  max-width: 700px;
  font-size: 0.95rem;
}

.footer {
  text-align: center;
  padding: 18px;
  font-size: 0.78rem;
  color: #555;
  border-top: 1px solid #1e1e3a;
}
</style>
