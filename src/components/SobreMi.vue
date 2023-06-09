<script>
export default{
    name: 'SobreMi',
    data(){
        return{
            title:'Sobre Mí',
            texto: '¡Hola a todos! Soy Jane, y actualmente vivo en la vibrante y emocionante ciudad de Tokio, Jápon. Me encanta capturar la esencia de la vida urbana a través de mi lente, explorando el contraste entre la arquitectura moderna y las tradiciones centenarias que conviven en esta metropolis única. Desde rascacielos deslumbrantes y calles bulliciosas hasta templos serenos y jardines tranquilos, encuentro inspiración en cada rincón de esta increíble ciudad.',
        }
    }
}
</script>

<template>
<div class="sobre-mi">
    <h1 class="title-about">{{ title }}</h1>
    <p class="txt-about">{{ texto }}</p>
</div>
</template>

<style scoped>
.sobre-mi{
    grid-area: 2 / 2 / 3 / 3;
    background: #fff;
    width: 60%;
    height: 25rem;
    border-radius: 10px;
    text-align: start;
    margin-right: 1%;
    margin-top: -5%;
}

.title-about{
    padding: 10px 15px;
    margin-top: 2rem;
    color: #bababa;
}

.txt-about{
    padding: 10px 15px;
}
</style>