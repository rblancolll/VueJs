<template>
    <div>
        <!-- Botones para cambiar entre componentes dinámicamente -->
        <div class="text-center my-3">
            <button class="btn btn-primary mx-2" @click="mostrarComponente('saludo')">
                Mostrar Saludo
            </button>
            <button class="btn btn-secondary mx-2" @click="mostrarComponente('contador')">
                Mostrar Contador
            </button>
        </div>


        <!-- Componente dinámico que se monta/desmonta según el valor de `componenteActual` -->
        <component v-if="componenteActual" :is="componenteActual"></component>
    </div>
</template>

<script>
// Importamos los componentes Saludo y Contador
import Saludo from './Saludo.vue';
import Contador from './Contador.vue';

export default {
    data() {
        return {
            componenteActual: 'saludo' // Estado inicial que define qué componente se muestra
        };
    },
    components: {
        // Registramos los componentes disponibles
        saludo: Saludo,
        contador: Contador
    },
    methods: {
        // Método para cambiar entre los componentes
        mostrarComponente(componente) {
            this.componenteActual = componente; // Actualiza qué componente se va a mostrar
        },

    }
};
</script>

<style scoped>
button {
    margin-top: 10px;
}
</style>
