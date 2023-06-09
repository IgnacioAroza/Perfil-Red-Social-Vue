<script>
import Swal from 'sweetalert2'
export default{
    name: 'Publicacion',
    props:{
        usuario: '',
    },
    data(){
        return{
            cantLikes: 200,
            botonPresionado: false,
            comentario: '',
            comentarios: [],
            userClass: 'nombre',
            commentClass: 'comentario',
        }
    },
    computed: {
        textoBoton(){
            return this.botonPresionado ? 'Ya No Me Gusta' : 'Me Gusta';
        },
    },
    methods:{
        sumarLike(){
            if(this.botonPresionado){
                this.cantLikes--;
            }else{
                this.cantLikes++;
            }
            this.botonPresionado = !this.botonPresionado;
        },
        agregarComentario(){
            if(this.comentario && this.usuario){
                this.comentarios.push({
                    usuario: this.usuario,
                    comentario: this.comentario,
                });
                this.comentario = '';
                this.error = '';
            }else{
                Swal.fire('Ingrese Usuario o Comentario');
            }
        },
        eliminarComentario(index){
            this.comentarios.splice(index, 1);
        },
    },
}
</script>

<template>
<div class="publicacion">
    <p class="publicado">Publicado hace 1 semana</p>
    <img src="../assets/img/publicacion.jpg" alt="" class="img-publicacion">
    <div class="mg">
        <button class="meGusta" id="meGusta" @click="sumarLike">{{ textoBoton }}</button>
        <p><strong class="cantLikes">{{ cantLikes }}</strong> Likes</p>
    </div>
    <div class="comentarios" id="comentarios">
        <h4>Comentarios</h4>
        <p class="comentario"><strong class="nombre">Juan Perez:</strong>  ¡Wow, esta foto de Tokio es Impresionante!&#127750;&#10024;</p>
        <p class="comentario"><strong class="nombre">Kathleen J Rennie:</strong> ¡Esta foto de Tokio es simplemente espectacular! Me trae tantos recuerdos.</p>
        <p class="comentario"><strong class="nombre">Diana Bell:</strong> ¡Espero que algún día pueda ver Tokio en persona!</p>
        <p v-if="error" style="color: red">{{ error }}</p>
        <ul style="list-style: none; padding: 0; padding-top: 10px;">
            <li v-for="(texto, index) in comentarios" :key="index">
                <div class="user-comment" style="display: inline">
                    <p :class="userClass">{{ texto.usuario }}: </p>
                    <p :class="commentClass">{{ texto.comentario }}</p>
                    <button @click="eliminarComentario(index)" class="btn-borrar">Eliminar</button>
                </div>
            </li>
        </ul>
    </div>
    <form class="inp-comentarios" @submit.prevent="agregarComentario">
        <input type="text" :value="this.usuario" class="user">
        <input type="text" placeholder="Deja tu comentario..." id="inp-coment" v-model="comentario">
        <button type="submit" id="comentar" class="comentar">Comentar</button>
    </form>
</div>
</template>

<style scoped>
.publicacion{
    grid-area: 2 / 1 / 4 / 2;
    background: #fff;
    width: 85%;
    height: 55rem;
    border-radius: 10px;
    margin-left: 25%;
    margin-top: -5%;
}

.img-publicacion{
    width: 80%;
    height: auto;
    margin: 2rem 0 0 5rem;
    border-radius: 10px;
    margin-top: 3rem;
}

.publicado{
    text-align: start;
    margin: 2.5rem 0 0 5rem;
}

.mg{
    display: flex;
    justify-content: space-between;
    margin: 1rem 5rem;
}

.meGusta{
    background: #0084EB;
    border: none;
    border-radius: 5px;
    color: #fff;
    width: 8rem;
    height: 2rem;
    font-weight: 600;
    cursor: pointer;
}

.comentarios{
    width: 85%;
    margin: 2.5rem 0 0 5rem;
}

.user-comment p{
    display: inline;
}

.comentario{
    padding-top: 10px;
}

.nombre{
    font-weight: 700;
}

.inp-comentarios{
    margin: 2.5rem 0 0 5rem;
    display: flex;
    justify-content: space-between;
    margin: 2rem 5rem;
}

.user{
    display: none;
}

.inp-comentarios input{
    background: #DDDDDD;
    border: none;
    border-radius: 10px;
    width: 70%;
    height: 2rem;
}

.btn-borrar{
    background: #DDDDDD;
    color: red;
    padding: 5px;
    border: none;
    border-radius: 5px;
    margin-left: 3rem;
    cursor: pointer;
}

.btn-borrar:hover{
    background: darkred;
}

.comentar{
    background: #0084EB;
    color: #fff;
    border: none;
    border-radius: 5px;
    height: 2rem;
    width: 6rem;
    cursor: pointer;
}

.comentar:hover{
    background: #0000ff;
    transition: 0.3s;
}
</style>