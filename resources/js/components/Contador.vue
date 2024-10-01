<template>
  <!-- Estructura de una tarjeta similar a la del saludo -->
  <div class="card">
    <!-- Encabezado con estilo diferente, usando un fondo azul claro -->
    <div class="card-header bg-info text-white text-center">
      <h4>Contador Dinámico</h4>
    </div>
    <!-- Cuerpo de la tarjeta con el valor del contador y dos botones -->
    <div class="card-body text-center">
      <h2>{{ contador }}</h2> <!-- Muestra el valor actual del contador -->
      <button class="btn btn-success mx-2" @click="incrementar">+</button>
      <!-- Botón para incrementar el contador -->
      <button class="btn btn-danger mx-2" @click="decrementar">-</button>
      <!-- Botón para decrementar el contador -->
    </div>
  </div>
</template>

<script>
export default {
  // Definimos el estado inicial
  data() {
    return {
      contador: 0 // Valor inicial del contador
    };
  },
  methods: {
    // Método para incrementar el contador
    incrementar() {
      this.contador++;
    },
    // Método para decrementar el contador (sin bajar de 0)
    decrementar() {
      if (this.contador > 0) {
        this.contador--;
      }
    }
  }
};
</script>

<style scoped>
/* Estilos similares a los del componente de saludo */
.card {
  border-radius: 12px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}
</style>
