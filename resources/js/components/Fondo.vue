<template>
   <h1 class="text-center">Fondo con Boostrap</h1>
    <div class="container mt-5">
        <!-- Div dinámico controlado por la caja de texto -->
        <div class="text-white p-3" :class="[inputClass || 'bg-warning']">
            <p>
                Lorem ipsum dolor sit amet consectetur adipisicing elit. Minus harum
                voluptate perspiciatis illum sint voluptates quia consequatur.
            </p>
        </div>

        <!-- Caja de texto para cambiar la clase del div superior -->
        <input type="text" class="form-control my-3" placeholder="Escribe una clase de fondo..." v-model="inputClass" />

        <!-- Div controlado por el botón -->
        <div class="p-3 text-white mt-3" :class="[color ? 'bg-info' : 'bg-success']">
            <p>
                Lorem ipsum dolor sit amet consectetur adipisicing elit. Earum
                dignissimos maiores dicta a perspiciatis eaque iure.
            </p>
        </div>

        <!-- Botón para cambiar de color en el div inferior -->
        <button class="btn btn-primary mt-3" @click="toggleColor">Cambiar</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            inputClass: '', // Clase ingresada por el usuario que afecta el div superior
            color: true,    // Alterna entre true/false para cambiar la clase del div inferior
        };
    },
    methods: {
        toggleColor() {
            // Alterna entre bg-info y bg-success en el div inferior
            this.color = !this.color;
        },
    },
};
</script>

<style scoped>
/* Estilos adicionales si los necesitas */
</style>
