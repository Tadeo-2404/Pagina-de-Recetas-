<template>
  <div class="hero d-flex flex-column justify-content-center align-items-center">
    <div class="hero__wrapper container-fluid d-flex flex-column justify-content-center align-items-center">
        <div class="d-flex flex-column justify-content-center align-items-center">
          <div class="row mb-3">
                <h2 class="text-center">Las Mejores recetas para empezar bien tu dia</h2>
          </div>
          <div class="row">
            <form class="d-flex">
               <input class="form-control me-2" type="text" placeholder="Buscar recetas" id="input">
               <button class="btn btn-success" type="button" @click="crearBloque">Buscar</button>
            </form>
          </div>
        </div>
    </div>
  </div>
</template>

<script>
import JSONData from '@/db/db.json'
export default {
   name: "Hero-Section",
   methods: {
    crearBloque() {
      let busqueda = document.querySelector('#input').value;
      busqueda = busqueda.toLowerCase();

      const ArregloRecetas = [];
      let arrRecetas = [];
      JSONData.recetas.map((tipo) => {
        tipo.recetas.map((receta) => ArregloRecetas.push(receta));
      });

      ArregloRecetas.find((receta) => {
        const nombre = receta.nombre.toLowerCase();
        if (nombre.includes(busqueda)) {
          arrRecetas.push(receta);
        }
      });

      this.$emit('generarHTML', true, busqueda);
      this.$emit('actualizarArreglo', arrRecetas);  
    }
   }
}
</script>

<style>

</style>