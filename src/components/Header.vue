<script>
export default{
    props:{
        usuario: '',
    },
    data(){
        return{
            usuario: '',
        }
    },
}
</script>

<template>
    <header>
        <img src="../assets/img/logo.png" alt="" id="logo">
        <input type="text" placeholder="Ingresa tu usuario..." id="inpUsuario" v-model="usuario" @input="$emit('update:usuario', usuario)">
    </header>
</template>

<style scoped>
header{
    background: #0084EB;
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 4rem;
    width: 100%;
    box-shadow: 0px 6px 10px 0px rgba(0,0,0,0.6);
}
#logo{
    margin: 10rem;
    height: 1.8rem;
}

#inpUsuario{
    margin: 10rem;
    height: 1.8rem;
    border: none;
    border-radius: 5px;
    text-align: center;
}
</style>