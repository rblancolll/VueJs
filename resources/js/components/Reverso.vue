<template>
    <h1 class="text-center">Mensaje Invertido</h1>

        <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <!-- Input para escribir el mensaje -->
                <div class="card my-3">
                    <div class="card-header">Mensaje Invertido</div>
                    <div class="card-body">
                        <input
                            v-model="mensaje"
                            type="text"
                            class="form-control mb-3"
                            placeholder="Escribe un mensaje"
                        />
                        <p><strong>Mensaje Invertido:</strong> {{ mensajeInvertido }}</p>
                    </div>
                </div>

                <!-- Barra de progreso con botones para incrementar o disminuir -->
                <div class="card my-3">
                    <div class="card-header">Progreso</div>
                    <div class="card-body">
                        <div class="progress mb-3" role="progressbar" :aria-valuenow="progreso" aria-valuemin="0" aria-valuemax="100">
                            <div class="progress-bar" :class="progresoColor" :style="{ width: progreso + '%' }">
                                {{ progreso }}%
                            </div>
                        </div>

                        <button @click="incrementar" class="btn btn-success mx-2">+</button>
                        <button @click="decrementar" class="btn btn-danger mx-2">-</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            mensaje: "", // Mensaje escrito por el usuario
            progreso: 0, // Valor del progreso
        };
    },
    computed: {
        // Computed para invertir el mensaje
        mensajeInvertido() {
            return this.mensaje.split("").reverse().join("");
        },
        // Computed para cambiar el color de la barra de progreso
        progresoColor() {
            if (this.progreso <= 10) {
                return "bg-success"; // Verde
            } else if (this.progreso > 10 && this.progreso <= 25) {
                return "bg-warning"; // Naranja
            } else {
                return "bg-purple"; // Morado
            }
        },
    },
    methods: {
        // Método para incrementar el progreso
        incrementar() {
            if (this.progreso < 100) {
                this.progreso += 5;
            }
        },
        // Método para decrementar el progreso
        decrementar() {
            if (this.progreso > 0) {
                this.progreso -= 5;
            }
        },
    },
};
</script>

<style scoped>
/* Personalizando el color morado para el progreso posterior al 25% */
.bg-purple {
    background-color: purple !important;
}
</style>
