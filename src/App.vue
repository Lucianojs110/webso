<template>
  <div id="app">
    <router-view />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  min-height: 100vh;
  background-image: url('~@/assets/fondo.jpeg');
  background-size: cover; /* Ajusta la imagen al tamaño del elemento */
  background-position: center; /* Centra la imagen */
  background-image: linear-gradient(rgba(58, 205, 202, 0.5), rgba(0, 0, 0, 0.5)), url('~@/assets/fondo.jpeg'); 
}
</style>
