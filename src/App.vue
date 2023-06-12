<script>
import Header from './components/Header.vue';
import InfBasica from './components/InfBasica.vue';
import Publicacion from './components/Publicacion.vue';
import SobreMi from './components/SobreMi.vue';

export default{
    name: 'App',
    components:{
    Header,
    InfBasica,
    Publicacion,
    SobreMi,
    InfBasica
},
    data(){
        return{
            usuario: '',
        }
    },
    methods:{
        updateUsuario(nuevoUsuario){
            this.usuario = nuevoUsuario;
        }
    },
}
</script>

<template>
<Header @update:usuario = "updateUsuario"></Header>
<section class="section">
    <InfBasica></InfBasica>
    <Publicacion :usuario="usuario"></Publicacion>
    <SobreMi></SobreMi>
</section>
</template>

<style>
@import './assets/main.css';
</style>
