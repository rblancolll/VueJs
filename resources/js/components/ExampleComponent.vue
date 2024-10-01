<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header">{{ titulo }}</div>

                    <div class="card-body">
                        <!-- Lista de frutas -->
                        <ul class="list-group mb-3">
                            <!-- Recorrer la lista de frutas con v-for -->
                            <li
                                v-for="(fruta, index) in frutas"
                                :key="fruta.nombre"
                                class="list-group-item d-flex justify-content-between align-items-center"
                            >
                                <!-- Contenedor flex para mantener nombre, input y botón alineados -->
                                <div class="d-flex align-items-center">
                                    <!-- Nombre de la fruta -->
                                    <span class="mr-3">{{ fruta.nombre }}</span>

                                    <!-- Input para modificar la cantidad -->
                                    <input
                                        type="number"
                                        v-model.number="fruta.cantidad"
                                        class="form-control w-25 mr-3 text-center"
                                        @input="verificarCantidad(index)"
                                    />
                                </div>

                                <!-- Botón para aumentar la cantidad, centrado y siempre visible -->
                                <button
                                    @click="incrementarCantidad(index)"
                                    class="btn btn-sm btn-success mx-3"
                                >
                                    +
                                </button>

                                <!-- Mostrar cantidad disponible o 'Sin stock' si cantidad es 0 -->
                                <span v-if="fruta.cantidad > 0" class="badge badge-primary badge-pill">{{ fruta.cantidad }}</span>
                                <span v-else class="badge badge-danger badge-pill">Sin stock</span>
                            </li>
                        </ul>

                        <!-- Formulario para agregar una nueva fruta -->
                        <input
                            v-model="nuevaFruta"
                            type="text"
                            class="form-control mb-2"
                            placeholder="Nueva fruta"
                        >
                        <input
                            v-model.number="cantidadFruta"
                            type="number"
                            class="form-control mb-2"
                            placeholder="Cantidad"
                            @input="verificarNuevaFrutaCantidad"
                        >
                        <button @click="agregarFruta" class="btn btn-primary">Agregar Fruta</button>

                        <!-- Mostrar el total de frutas -->
                        <p class="mt-3"><strong>TOTAL: {{ totalFrutas }}</strong></p>
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
            titulo: 'Lista de Frutas',
            frutas: [
                { nombre: 'Pera', cantidad: 10 },
                { nombre: 'Manzana', cantidad: 4 },
                { nombre: 'Platano', cantidad: 11 }
            ],
            nuevaFruta: '', // Nombre de la nueva fruta
            cantidadFruta: 0 // Cantidad de la nueva fruta
        }
    },
    methods: {
        // Método para agregar una nueva fruta a la lista
        agregarFruta() {
            if (this.nuevaFruta.trim() !== '') {
                // Añadimos la nueva fruta solo si el nombre no está vacío
                this.frutas.push({
                    nombre: this.nuevaFruta,
                    cantidad: this.cantidadFruta > 0 ? this.cantidadFruta : 0 // Evitamos cantidades negativas
                });
                this.nuevaFruta = ''; // Limpiamos los campos después de agregar
                this.cantidadFruta = 0;
            }
        },
        // Método para incrementar la cantidad de una fruta
        incrementarCantidad(index) {
            this.frutas[index].cantidad++;
        },
        // Método para verificar que la cantidad no sea negativa al editar
        verificarCantidad(index) {
            if (this.frutas[index].cantidad < 0) {
                this.frutas[index].cantidad = 0; // Si es menor a 0, la cantidad se resetea a 0
            }
        },
        // Verificación de la cantidad de la nueva fruta
        verificarNuevaFrutaCantidad() {
            if (this.cantidadFruta < 0) {
                this.cantidadFruta = 0; // Si es menor a 0, la cantidad se resetea a 0
            }
        }
    },
    computed: {
        // Computamos el total de todas las frutas en stock
        totalFrutas() {
            return this.frutas.reduce((total, fruta) => total + fruta.cantidad, 0);
        }
    },
    mounted() {
        console.log('Lista de Frutas cargada.');
    }
}
</script>

<style scoped>
/* Para mantener el input y los botones alineados */
.form-control.w-25 {
    width: 60px;
    text-align: center;
}
.list-group-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.mx-3 {
    margin-left: 1rem;
    margin-right: 1rem;
}
</style>
