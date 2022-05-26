<template>
    <div class="card " style="width: 20rem; height: 26rem;" >
      <img alt="titulo" :src="getImgUrl()" class="card-img-top rounded" style="" height="200"  />
         <div class="card-body">
    <h3 class="card-title">{{ titulo}}</h3>
    <p class="card-text">{{ descripcion}}</p>
    <h5>${{precio}}</h5>


        </div>
        <button type="button" class="btn btn-info" @click="AgregarAlCarrito()">Agregar</button>
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
            type: Number,
            required: true,
        },
        descripcion: {
            type: String,
            required: true,
        },
        id: {
            type: Number,
            required: true,
        },
        cantidad: {
            type: Number,
            required: true,
        },
    },

    methods: {
        getImgUrl() {
            return require(`@/assets/images/${this.nombreImagen}`);
        },
        AgregarAlCarrito() {
            this.$emit("agregar-al-carrito", this.id);
        },
    },
};
</script>

<style>

</style>
