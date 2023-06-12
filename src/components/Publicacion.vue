<script>
import Swal from 'sweetalert2';

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
            comentarios: [
                {usuario: 'Juan Perez', comentario: '¡Wow, esta foto de Tokio es Impresionante!', esDueño: false},
                {usuario: 'Kathleen J Rennie', comentario: '¡Esta foto de Tokio es simplemente espectacular! Me trae tantos recuerdos.', esDueño: false},
                {usuario: 'Diana Bell', comentario: '¡Espero que algún día pueda ver Tokio en persona!', esDueño: false},
            ],
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
                    esDueño: true,
                });
                this.comentario = '';
                this.error = '';
            }else{
                Swal.fire('Ingrese Usuario y Comentario');
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
        <button class="meGusta" @click="sumarLike">{{ textoBoton }}</button>
        <p class="likes">{{ cantLikes }} Likes</p>
    </div>
    <div class="comentarios">
        <h4>Comentarios</h4>
        <ul style="list-style: none; padding: 0; padding-top: 10px;">
            <li v-for="(texto, index) in comentarios" :key="index">
                <div class="user-comment" style="display: inline">
                    <p :class="userClass">{{ texto.usuario }}: </p>
                    <p :class="commentClass">{{ texto.comentario }}</p>
                    <button v-if="texto.esDueño" @click="eliminarComentario(index)" class="btn-borrar">Eliminar</button>
                </div>
            </li>
        </ul>
    </div>
    <form class="inp-comentarios" @submit.prevent="agregarComentario">
        <input type="text" :value="this.usuario" class="user">
        <input type="text" placeholder="Deja tu comentario..." v-model="comentario">
        <button type="submit" class="comentar">Comentar</button>
    </form>
</div>
</template>

<style scoped>
.publicacion{
    grid-area: 2 / 1 / 4 / 2;
    background: #fff;
    width: 85%;
    height: auto;
    margin-bottom: 2rem;
    border-radius: 10px;
    margin-left: 25%;
    margin-top: -5%;
}

.likes, .comentarios h4{
    font-weight: 700;
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
    font-weight: 700;
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

.meGusta:hover{
    background: #0000ff;
    transition: 0.3s;
}

.comentarios{
    width: 85%;
    margin: 2.5rem 0 0 5rem;
}

.user-comment p{
    display: inline;
}

.nombre{
    font-weight: 700;
}

li{
    padding-top: 10px;
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

@media (max-width: 1024px) {
    .publicacion{
        display: flex;
        flex-direction: column;
    }
    .img-publicacion{
        margin: auto;
    }
    .comentarios{
        margin: auto;
    }
    .inp-comentarios{
        width: 20rem;
        margin: auto;
    }
}

@media (max-width: 768px){
    .publicacion{
        margin-left: -10%;
        margin-top: 5%;
        height: auto;
        width: 80%;
    }

    .publicacion img{
        padding-top: 20px;
    }
    .publicado{
        margin-left: 35%;
    }
    .mg{
        margin-left: 12%;
        width: auto;
    }
    .meGusta{
    background: #0084EB;
    border: none;
    border-radius: 5px;
    color: #fff;
    width: 8rem;
    height: 2rem;
    font-weight: 400;
    cursor: pointer;
    font-size: 12px;
    }

    .meGusta:hover{
        background: #0000ff;
        transition: 0.3s;
    }
    .inp-comentarios{
        width: 70%;
        margin: 2rem 5rem;
    }
    .inp-comentarios button{
        width: 5rem;
        text-align: center;
        font-size: 12px;
    }
}

@media (max-width: 425px){
    .publicado{
        margin-left: 20%;
    }
    .inp-comentarios{
        width: 80%;
        margin: 2rem 2rem;
    }
}
</style>