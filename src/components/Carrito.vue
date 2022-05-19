<template>
<div>
 <nav class="navbar navbar-light " style="background-color: #CDF1F5;">
 <ul class="nav">
  <li class="nav-item">
    <button type="button" class="btn btn-primary">
  Items en carrito  <span class="badge badge-light">{{ productos.length }}</span>
</button>
  </li>
 </ul>
 </nav>
</div>
</template>

<script>

// {{ productos.length }}
export default {
    name: "Carrito",
    data() {
        return {
            productos: [],
        };
    },
    methods: {
        AgregarProducto(producto) {
            //TODO: Ver de sumar productos iguales
            let i = this.productos.findIndex((prod) => prod.id == producto.id);
            if (i >= 0) this.productos[i].cantidad += 1;
            else {
                producto.cantidad = 1;
                this.productos.push(producto);
            }
            console.log(`Producto "${producto.titulo}" agregado!`);
        },

    },

}
    </script>


<style scoped>

</style>
