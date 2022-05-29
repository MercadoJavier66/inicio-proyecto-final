<template>
    <div class="container">
         <div class="row align-items-start">
            <div class="card col" style="width: 18rem;">
                <div class="card-body">
                    <h5 class="card-title">Registrese para ingresar al sistema</h5>
                    <div>
                        <form>
                            <div class="mb-3">
                                <select class="form-select" v-model="rol">
                                    <option value="cliente" selected>Usuario de tipo cliente</option>
                                    <option value="admin">Usuario Administrador</option>
                                 </select>
                            </div>
                            <div class="mb-3">
                                <label class="form-label">Nombre</label>
                                <input type="text" class="form-control"  aria-describedby="emailHelp" v-model="nombre">
                            </div>
                            <!-- <div class="row" v-if='nombreValido != ""'>
                            <p class="datoinvalido">{{ nombreValido }}</p>
                            </div> -->
                            <div class="mb-3">
                                <label class="form-label">Correo electronico</label>
                                <input type="email" class="form-control" aria-describedby="emailHelp" v-model="email">
                            </div>
                            <div class="mb-3">
                                <label class="form-label">Contraseña</label>
                                <input type="password" class="form-control" v-model="password">
                            </div>
                        </form>
                    </div>
                    <button class="btn btn-success" @click="insertUsuario()">Agregar usuario</button>
                </div>
            </div>
        </div>
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
    name: "Registro",
    data(){
        return {
            nombre: null,
            email: null,
            password: null,
            rol: "cliente",
        }
    },
    methods:{
        async insertUsuario(){
            const usuario = await Vue.axios({
                method: 'post',
                url: 'https://628ee4bddc47852365360ef5.mockapi.io/api/v1/usuario',
                data:  {
                    "nombre": this.nombre,
                    "email": this.email,
                    "contrasena": this.password,
                    "tipoUsuario": this.rol,
                    },
                    // nombreValido: "",
                    // correoValido: "",
                    // contrasenaValida: "",
            });
            // return usuario
            console.log(usuario)
            this.nombre = null
            this.email = null
            this.password = null
            this.rol = "cliente"
        },
        // validarNombre(){
        //     const valnombre = /[a-zA-Z]{3,}\s[a-zA-Z]{3,}/g;
        //     if (valnombre.test(nombre)){
        //     this.nombreValido = "";
        //         return true;
        //     } else {
        //         this.nombreValido = "El Nombre y Apellido debe contener al menos 3 caracteres.";
        //         return false;
        //     }
        // },
        // validarCorreo() {
        //     const valcorreo = /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/;
        //    if (valcorreo.test(email)){
        //         this.correoValido = "";
        //         return true;
        //     } else {
        //         this.correoValido = "Mail incorrecto";
        //         return false;
        //     }

        // },
        // validarPass(){
        //     let reg_ex_password = /^(?=.*?[A-Z])(?=.*?[a-z])(?=.*?[0-9])(?=.*?[#?!@$%^&*-]).{8,}$/;
        //     if (reg_ex_password.test(password)){
        //         this.contrasenaValida = "";
        //         return true;
        //     } else {
        //         this.contrasenaValida = "La contraseña debe contener al menos 8 caracteres, una mayúscula, un caracter especial y un número."
        //         return false;
        //     }
        // },
    }
}
</script>

<style>

</style>
