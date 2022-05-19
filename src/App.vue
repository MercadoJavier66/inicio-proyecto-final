<template>
    <div id="app">
        <Titulo></Titulo>
         <Carrito
            ref="miCarrito"

        />

        <div class="contenedorProductos">
            <Producto
                v-for="(item, i) in productos"
                :key="i"
                :id="item.id"
                :titulo="item.titulo"
                :descripcion="item.descripcion"
                :precio="item.precio"
                :nombre-imagen="item.nombreImagen"
                @agregar-al-carrito="AgregarAlCarrito"
            >
            </Producto>
        </div>

    </div>
</template>

<script>





import Titulo from "./components/Titulo.vue";
import Producto from "./components/Producto.vue";
import Carrito from "./components/Carrito.vue";

export default {
    name: "App",
    props: [],
    components: {
        Carrito, Producto, Titulo,
    },

    data() {
        return {
            productos: [
                {
                    id: 1,
                    titulo: 'Vacio',
                    descripcion: 'Tierno vacio realizado a las brasas. Con papas fritas',
                    precio: 900 ,
                    nombreImagen: "vacio.jpg",

                },
                {
                    id: 2,
                    titulo: "Bondiola",
                    descripcion: "Bondiola de cerdo a la parrilla, con papas fritas",
                    precio: 700,
                    nombreImagen: "bondio.jpg",

                },
                {
                    id: 3,
                    titulo: "Matambre a la pizza",
                    descripcion: "Matambre de carne con salsa de tomate, mozzarela, jamon y huevo frito",
                    precio: 1200,
                    nombreImagen: "matambre.jpg",

                },
            ],
        };
    },
    methods: {
        AgregarAlCarrito(id) {
            let result = this.productos.find((prod) => {

                return prod.id == id;
            });
            if (result) {
                this.$refs.miCarrito.AgregarProducto(result);
            }
        },

    },
};
</script>

<style>
body {
    margin: 0;
}
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #111;
}
.contenedorProductos {
    display: flex;
    align-items: center;
    justify-content: center;
}
</style>
