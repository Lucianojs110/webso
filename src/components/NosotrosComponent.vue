<template>
  <div>
    <br /><br /><br /><br /><br />
    <h1 class="custom-heading">
      Nuestros servicios
    </h1>
    <div class="content">
      Desarrollamos nuestros servicios de manera personalizada y especializada.
      Para nosotros, cada proyecto que desarrollamos es un trabajo diferente,
      que requiere de nuestra máxima capacidad, talento, compromiso y trabajo en
      equipo. Es esto lo que hace que nuestros servicios sean únicos para cada
      proyecto.
    </div>

    <br>
    

    <div class="two-columns">
      <div class="column">
        <h2 class="custom-sub-heading">Desarrollo sitios web</h2>
        <div class="content">
          Desarrollamos todo tipo de sitios web. Sitios web landing page, sitios
          web institucionales, e-commerce, e-learning, y sitios 100%
          personalizados. Desarrollos con CMS o con código propio.
        </div>
        <br>
         <h2 class="custom-sub-heading">Aplicaciones mobile</h2>
        <div class="content">
          Realizamos aplicaciones mobile híbridas o bien PWA que estan en un gran auge. Desarrollos con tecnologias modernas, utilizacion de funcionalidades nativas de celular y multi plataforma.
        </div>
      </div>
      <div class="column">
        <h2 class="custom-sub-heading">Desarrollo de software web</h2>
        <div class="content">
          El desarrollo de software personalizado es lo que nos caracteriza.
          Realizamos sistemas de gestion web completamente a medida de las
          necesidades de cada cliente.
        </div>
        <br>
         <h2 class="custom-sub-heading">Diseño UI/UX</h2>
        <div class="content">
          Ponemos mucho énfasis en la interfaz y experiencia de usuario que tan importantes son hoy en dia. Desarrollando aplicaciones o sistemas con una gran aplicacion de diseño moderno y usabilidad.
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "NosotrosComponent",
};
</script>

<style scoped>
.custom-heading {
  font-family: Verdana, sans-serif;
  font-weight: 300;
  font-size: 22px;
  text-align: left;
  padding-left: 20px;
}

.custom-sub-heading {
  font-family: Verdana, sans-serif;
  font-weight: 300;
  font-size: 16px;
  text-align: left;
  padding-left: 20px;
}

.content {
  padding-left: 20px;
  color: #777;
  text-align: left;
  font-family: Verdana, sans-serif;
  font-weight: 300;
   font-size: 13px;
}

.two-columns {
  display: flex;
  color: #777;

}

.column {
  flex: 1;
  color: #777;

}

.column h2 {
  color: #333;
}

.column p {
  color: #333;
}


</style>
