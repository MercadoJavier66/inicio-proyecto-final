<template>
    <div class="col-6 col-sm-3">
        <div class="card" style="width: 18rem;">
            <img :src="nombreImagen" class="card-img-top" alt="...">
            <div class="card-body" style="height: 15rem;">
                <h5 class="card-title">{{ titulo }}</h5>
                <p class="card-text recorte-texto">{{ descripcion }}</p>
                <p class="card-text">${{ precio }}</p>
                <p class="card-text">Stock: {{ cantidad }}</p>
                <button class="btn btn-primary" @click="AgregarAlCarrito()">Agregar</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Producto",
    props: {
        titulo: {
            type: String,
            required: true,
        },
        nombreImagen: {
            type: String,
            required: true,
        },
        precio: {
            type: String,
            required: true,
        },
        descripcion: {
            type: String,
            required: true,
        },
        id: {
            type: String,
            required: true,
        },
        cantidad: {
            type: Number,
            required: true,
        },
    },

    methods: {
        AgregarAlCarrito() {
            this.$emit("agregar-al-carrito", this.id);
        },
    },
};
</script>

<style>
    .recorte-texto {
        overflow: hidden;
        display: -webkit-box;
        -webkit-line-clamp: 2;
        -webkit-box-orient: vertical;
    }
</style>
