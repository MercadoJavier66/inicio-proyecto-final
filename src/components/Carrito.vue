<template>
    <div>
        <nav class="navbar navbar-light " style="background-color: #CDF1F5;">
            <ul class="nav">
                <li class="nav-item">
                    <button type="button" class="btn btn-primary" @click="mostrarElementosDelCarrito()">
                        Items en carrito  <span class="badge badge-light">{{ cantidadProductosCarrito }}</span>
                    </button>
                </li>
            </ul>
        </nav>
        <div v-if="mostrarListado">
            <div class="m-4">
                <ol class="list-group">
                    <li class="list-group-item d-flex justify-content-between align-items-start" v-for="(prod, i) in productos" :key="i">
                        <div class="ms-2 me-auto">
                            <div class="fw-bold" style="text-align: left;">{{prod.titulo}}</div>
                            {{prod.descripcion}}
                            <div style="text-align: left;">
                                Precio unitario: $ {{prod.precio}}
                            </div>
                        </div>
                        <span class="badge bg-primary rounded-pill">{{prod.cantidad}}</span>
                    </li>
                    <li class="list-group-item d-flex justify-content-between align-items-start">
                        <div class="ms-2 me-auto">
                            <div class="fw-bold">Total</div>
                            $ {{totalAPagar}}
                        </div>
                    </li>
                </ol>
            </div>
        </div>
    </div>
</template>

<script>


export default {
    name: "Carrito",
    data() {
        return {
            productos: [],
            mostrarListado: false
        };
    },
    computed: {
        cantidadProductosCarrito(){
            let total = 0
            this.productos.forEach(e => {
                total += e.cantidad
            })
            return total
        },
        totalAPagar(){
            let total = 0
            this.productos.forEach(e => {
                total += e.cantidad * e.precio
            })
            return total
        }
    },
    methods: {
        AgregarProducto(producto) {
            //TODO: Ver de sumar productos iguales
            let productoEnCarrito = this.productos.find(prod => prod.id == producto.id);
            const nuevoProducto = {...producto}
                producto.cantidad--;
            if (productoEnCarrito) {
                productoEnCarrito.cantidad++
            } else {
                nuevoProducto.cantidad = 1;
                this.productos.push(nuevoProducto);
            }
        },
        mostrarElementosDelCarrito(){
            this.mostrarListado = !this.mostrarListado
        }
    },

}
    </script>


<style scoped>

</style>
