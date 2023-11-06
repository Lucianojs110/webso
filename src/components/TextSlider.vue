<template>
  <div class="text-slider">
    <div class="text-container" :style="{ animationDuration: slideDuration }">
      <div v-for="(item, index) in textList" :key="index" class="text-item">
        <h1>{{ item }}</h1>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TextSlider",
  props: {
    textList: Array, // Lista de textos que se mostrarán en el slider
    slideDuration: String, // Duración de la animación de desplazamiento
  },
};
</script>

<style scoped>
.text-container {
  display: flex;
  transition: transform 0.5s ease;
  word-break: break-word;
  white-space: normal;
  
}

.text-item {
  white-space: normal; /* Permite que el texto se ajuste automáticamente al ancho del div */
  flex-shrink: 0;
  padding: 0 10px; /* Espacio entre los textos */
  word-break: break-word;

}
.text-item h1 {
  color: white;
 
}

@keyframes slideText {
  0% {
    transform: translateX(100%);
  }
  100% {
    transform: translateX(-100%);
  }
}
</style>
