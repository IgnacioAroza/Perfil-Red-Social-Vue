<script>
import { useCssModule } from 'vue';

export default{
    name: 'InfBasica',
    data(){
        return {
            nombre: 'Jane Doe',
            email: 'jane_doe@email.com',
            nacimiento: '01/05/1996',
            telefono: '918-936-9585',
            ciudad: 'Tokyo, Japon',
            seguir: false,
        }
    },
    computed:{
        seguirTexto(){
            return this.seguir ? 'Dejar de seguir' : 'Seguir';
        }
    },
    methods:{
        Seguir(){
            this.seguir = !this.seguir;
        }
    },
}
</script>

<template>
<div class="inf-basica">
    <div class="foto">
        <img src="../assets/img/imgPerfil.jpg" alt="">
    </div>
    <div class="datos">
        <h1>{{ nombre }}</h1>
        <p><strong>Email</strong>: {{ email }}</p>
        <p><strong>Fecha de nacimiento</strong>: {{ nacimiento }}</p>
        <p><strong>Teléfono</strong>: {{ telefono }}</p>
        <p><strong>Ciudad</strong>: {{ ciudad }}</p>
        <p>Trabajando en Lawn N</p>
    </div>
    <button id="seguir" @click="Seguir()">{{ seguirTexto }}</button>
</div>
</template>

<style scoped>
.inf-basica{
    grid-area: 1 / 1 / 2 / 3;
    background: #fff;
    height: 15rem;
    width: 80%;
    display: flex;
    align-items: center;
    border-radius: 10px;
    margin-top: 3rem;
    position: relative;
}
.foto{
    padding: 10px 10px;
}
.foto img{
    width: 12rem;
    height: 12rem;
    border-radius: 50%;
    border: 3px solid #0084EB;
    margin-left: 3rem;
}

.inf-basica button{
    border: none;
    border-radius: 10px;
    height: 2.3rem;
    width: 9rem;
    background: #0084EB;
    color: #fff;
    position: absolute;
    left: 80%;
    top: 70%;
    cursor: pointer
}

.inf-basica button:hover{
    background: #0000ff;
    transition: 0.3s;
}

.datos{
    margin-left: 1rem;
}

.datos p, h1{
    padding: 5px;
    text-align: left;
}

strong{
    font-weight: 700;
}

@media (max-width: 768px){
    .inf-basica{
        margin-left: -10%;
    }
    .foto img{
        margin: 3%;
    }
    .inf-basica button{
    border: none;
    border-radius: 10px;
    height: 2.3rem;
    width: 6rem;
    background: #0084EB;
    color: #fff;
    position: absolute;
    left: 80%;
    top: 70%;
    cursor: pointer
    }

.inf-basica button:hover{
    background: #0000ff;
    transition: 0.3s;
    }
}
@media (max-width: 425px){
    .inf-basica{
        font-size: 12px;
        position: static;
    }
    .foto img{
        width: 8rem;
        height: auto;
    }
    .datos{
        position: absolute;
        left: 35%;
        top: 27%;
    }
    .inf-basica button{
        height: 2rem;
        width: 5rem;
        left: 60%;
        font-size: 12px;
    }
}
</style>