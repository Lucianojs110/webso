<template>
  <div>
    <div class="home">
      <div class="row" style="min-height: 80vh">
        <div
          class="col-1"
          style="
            background-color: #fff;
            width: 100px;
            z-index: 2;
            display: flex;
            flex-direction: column;
            align-items: flex-end;
            justify-content: flex-end;
          "
        >
          <img
            src="/square-instagram.svg"
            alt="Logo"
            style="
              max-height: 30%;
              max-width: 30%;
              vertical-align: middle;
              margin-right: 20px;
            "
          />
          <br />
          <img
            src="/square-facebook.svg"
            alt="Logo"
            style="
              max-height: 30%;
              max-width: 30%;
              vertical-align: middle;
              margin-right: 20px;
            "
          />
          <br />
          <img
            src="/whatsapp.svg"
            alt="Logo"
            style="
              max-height: 30%;
              max-width: 30%;
              vertical-align: middle;
              margin-right: 20px;
              margin-bottom: 20px;
            "
          />
        </div>
        <div class="col-10" style="background-color: transparent">
          <div class="row" style="background-color: #fff">
            <div
              class="col-3 text-left"
              style="
                background-color: #fff;
                z-index: 2;
                display: flex;
                align-items: center;
              "
            >
              <!-- Contenido de ancho 2 -->
              <img
                src="/logo.png"
                alt="Logo"
                style="max-height: 60%; max-width: 60%; vertical-align: middle"
              />
              <font-awesome-icon icon="fa-solid fa-xmark" />
            </div>

            <div
              class="col-9"
              style="
                background-color: #fff;
                z-index: 2;
                height: 90px;
                border-bottom: 1px solid gray;
                border-right: 1px solid gray;
              "
            >
              <ul class="menu">
                <li>
                  <a href="#" @click="showAdditional('NosotrosComponent')"
                    >Nosotros</a
                  >
                </li>
                <li>
                  <a href="#" @click="showAdditional('TrabajoComponent')"
                    >Trabajos</a
                  >
                </li>
                <li>
                  <a href="#" @click="showAdditional('ContactoComponent')"
                    >Contacto</a
                  >
                </li>
              </ul>
            </div>
          </div>

          <!--aca va contenido home -->
          <div class="text-slider">
            <div
              class="text-container"
              :style="{
                animationDuration: slideDuration,
                transform: `translateX(${translateX})`,
              }"
            >
              <div class="text-item"><h1>{{ currentText }}</h1></div>
            </div>
          </div>

          <div
            class="additional-content"
            ref="additionalContent"
            :class="{ active: showAdditionalContent }"
          >
            <!-- Usamos el componente dinámico para mostrar el contenido -->

            <component :is="selectedContent" />
            <button @click="hideAdditional" class="close-button">X</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import NosotrosComponent from "@/components/NosotrosComponent.vue";
import TrabajoComponent from "@/components/TrabajoComponent.vue";
import ContactoComponent from "@/components/ContactoComponent.vue";
import TextSlider from "@/components/TextSlider.vue";

export default {
  name: "HomePage",
  components: {
    NosotrosComponent,
    TrabajoComponent,
    ContactoComponent,
    TextSlider,
  },
  data() {
    return {
      selectedContent: null, // Inicialmente no muestra ningún contenido
      showAdditionalContent: false, // Inicialmente oculto
      textList: ["Somos una agencia de desarrollo", "Creamos soluciones de gestion a medida", "Creamos Software de calidad"],
      currentTextIndex: 0,
      currentText: "",
      translateX: "0%",
    };
  },

  mounted() {
    this.updateText();
    this.startInterval();
  },
  methods: {
    showAdditional(content) {
      // Actualiza el contenido adicional y muestra el div
      this.selectedContent = content;
      this.showAdditionalContent = true;
    },
    hideAdditional() {
      this.selectedContent = null; // Oculta el contenido
      this.showAdditionalContent = false;
    },
    updateText() {
      this.currentText = this.textList[this.currentTextIndex];
    },
    startInterval() {
      setInterval(() => {
        this.translateX = "100%"; // Desplazamiento a la derecha
        setTimeout(() => {
          this.currentTextIndex =
            (this.currentTextIndex + 1) % this.textList.length;
          this.updateText();
          this.translateX = "0%"; // Reiniciar a la posición original
        }, 500); // Pausa antes de cambiar de texto (ajusta el valor según tus necesidades)
      }, 5000); // Cambia de texto cada 5 segundos (ajusta el valor según tus necesidades)
    },
  },
};
</script>

<style>
/* Agrega un margen abajo de 100px y un margen a la izquierda de 100px a la clase "home" */
.home {
  margin-bottom: 100px;
  margin-right: 100px;
}
.menu {
  margin-top: 35px;
  margin-right: 45px;
  list-style: none;
  padding: 0;
  text-align: right;
  font-size: 15px;
}

.menu li {
  display: inline; /* Muestra los elementos en línea uno al lado del otro */
  margin-left: 10px; /* Agrega un margen entre los elementos */
}

.menu a {
  text-decoration: none;
  color: #333;
}

.additional-content {
  position: absolute;
  top: 0;
  right: 0;
  width: 70%;
  height: 100%;
  background-color: #fff;
  z-index: 1;
  transform: translateX(100%);
  transition: transform 0.3s ease-in-out;
  overflow: hidden;
}

body {
  overflow-x: hidden; /* Evita que se desplace horizontalmente */
}

/* Estilos para mostrar el div de contenido adicional */
.additional-content.active {
  display: block;
  transform: translateX(0);
}

.close-button {
  position: absolute;
  top: 10px;
  right: 10px;
  background-color: transparent; /* Cambia el color de fondo según tus preferencias */
  color: gray; /* Cambia el color del texto según tus preferencias */
  border: solid 1px gray;
  padding: 5px 10px;
  cursor: pointer;
  font-size: 20px;
}

.text-slider {
  overflow: hidden;
    width: 60%;
}

.text-container {
  margin-top: 18%;
  margin-left: 5%;
  display: flex;
  transition: transform 0.5s ease;
  word-break: break-word;
  white-space: normal;
  
 
}


.text-item h1 {
  color: white;
  text-align: left;
  font-size: 50px;
   font-weight: 800;
   font-family: Verdana, sans-serif;
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
