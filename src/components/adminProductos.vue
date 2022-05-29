<template>
    <div>
        <h1>Lista de Productos</h1>
        <table class="table table-success table-striped">
            <thead>
                <tr>
                <th scope="col">ID</th>
                <th scope="col">Titulo</th>
                <th scope="col">descripcion</th>
                <th scope="col">Imagen</th>
                <th scope="col">Precio</th>
                <th scope="col">cantidad</th>
                <th scope="col">Accion</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(prod, indice) in productos" :key="indice">
                    <th scope="row">{{prod.id}}</th>
                    <td>{{prod.titulo}}</td>
                    <td>{{prod.descripcion}}</td>
                    <td> <img :src="prod.nombreImagen" :alt="prod.nombreImagen" style="width: 150px;"></td>
                    <td>{{prod.precio}}</td>
                    <td>{{prod.cantidad}}</td>
                    <td>
                        <button type="button" class="btn btn-outline-success">Modificar</button>
                        <button type="button" class="btn btn-outline-danger">Eliminar</button>
                    </td>
                    </tr>
            </tbody>
        </table>
    </div>
</template>

<script>

/**
 * importo axios
 */
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'
Vue.use(VueAxios, axios)

export default {
    name: 'adminProductos',
    data(){
        return {
            productos: []
        }
    },
    methods:{
        async getProductos(){
            const productos = await Vue.axios({
                method: 'get',
                url: 'https://628ee4bddc47852365360ef5.mockapi.io/api/v1/productos',
            });
            this.productos = productos.data
        },
        async modifProducto(){
          const prod = await Vue.axios({
            method: 'put',
            url: 'https://628ee4bddc47852365360ef5.mockapi.io/api/v1/productos',
            data:  {
                "titulo": this.titulo,
                "descripcion": this.descripcion,
                "nombreImagen": this.nombreImagen,
                "precio": this.precio,
                "cantidad": this.cantidad,
            }
        });
        },
    },
    created(){
        this.getProductos()
    }
}
</script>

<style>

</style>
