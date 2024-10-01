<template>
    <h1 class="text-center">Lifecycle
    <br><br> <br><br>
    <div v-if="!destroyed">
        <h3>{{ saludo }}</h3>

        <!-- Botón para cambiar el saludo -->
        <button class="btn btn-primary" @click="cambiarSaludo">Cambiar</button>

        <!-- Botón para destruir el componente -->
        <button class="btn btn-danger" @click="destruir">Destruir</button>
    </div>
    </h1>
</template>

<script>
export default {
    data() {
        return {
            saludo: 'soy ciclo de vida de Vue', // Saludo inicial
            destroyed: false, // Estado para controlar si el componente está destruido
        };
    },
    beforeCreate() {
        console.log("beforeCreate"); // Log en consola antes de que el componente sea creado
    },
    created() {
        console.log("created"); // Log en consola después de que el componente ha sido creado
    },
    beforeMount() {
        console.log("beforeMount"); // Log en consola antes de que el componente sea montado
    },
    mounted() {
        console.log("mounted"); // Log en consola después de que el componente ha sido montado
    },
    beforeUpdate() {
        console.log("beforeUpdate"); // Log en consola antes de que el componente sea actualizado
    },
    updated() {
        console.log("updated"); // Log en consola después de que el componente ha sido actualizado
    },
    beforeUnmount() {
        console.log("beforeUnmount"); // Log en consola antes de que el componente sea destruido
    },
    unmounted() {
        console.log("unmounted"); // Log en consola después de que el componente ha sido destruido
    },
    methods: {
        cambiarSaludo() {
            this.saludo = 'saludo cambiado'; // Cambia el saludo al hacer clic
        },
        destruir() {
            // Cambia el estado para ocultar el componente
            this.destroyed = true; // Cambia a true para ocultar el componente
            console.log("Destruyendo el componente..."); // Mensaje en consola al destruir
        },
    },
};
</script>

<style scoped>
/* Estilos opcionales para el componente */
</style>
