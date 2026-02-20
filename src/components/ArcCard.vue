<template>
  <div class="arc-card">
    <div class="card-header">
      <h3 class="card-nombre">{{ arc.nombre }}</h3>
      <span class="card-tipo">{{ arc.tipo }}</span>
    </div>
    <div class="card-body">
      <p class="card-descripcion">{{ arc.descripcion }}</p>
      <ul class="card-datos">
        <li><strong>Peligrosidad:</strong> <span :class="peligrosidadClase">{{ arc.peligrosidad }}</span></li>
        <li><strong>Habilidad:</strong> {{ arc.habilidad }}</li>
        <li><strong>Debilidad:</strong> {{ arc.debilidad }}</li>
      </ul>
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  arc: {
    type: Object,
    required: true
  }
})

const peligrosidadClase = computed(() => {
  const mapa = {
    'Baja': 'nivel-bajo',
    'Media': 'nivel-medio',
    'Alta': 'nivel-alto',
    'Crítica': 'nivel-critico'
  }
  return mapa[props.arc.peligrosidad] || ''
})
</script>

<style scoped>
.arc-card {
  background-color: #16213e;
  border: 1px solid #2a2a4a;
  border-radius: 6px;
  padding: 20px;
  transition: border-color 0.2s;
}

.arc-card:hover {
  border-color: #e63946;
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 12px;
  border-bottom: 1px solid #2a2a4a;
  padding-bottom: 10px;
}

.card-nombre {
  margin: 0;
  font-size: 1.15rem;
  color: #e0e0e0;
}

.card-tipo {
  font-size: 0.78rem;
  background-color: #0f3460;
  color: #a0c4ff;
  padding: 3px 10px;
  border-radius: 12px;
}

.card-descripcion {
  font-size: 0.88rem;
  color: #b0b0c0;
  line-height: 1.5;
  margin-bottom: 12px;
}

.card-datos {
  list-style: none;
  padding: 0;
  margin: 0;
  font-size: 0.85rem;
  color: #c0c0d0;
  display: flex;
  flex-direction: column;
  gap: 5px;
}

.nivel-bajo    { color: #6bcb77; }
.nivel-medio   { color: #ffd166; }
.nivel-alto    { color: #f4845f; }
.nivel-critico { color: #e63946; font-weight: bold; }
</style>
