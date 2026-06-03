<script setup>
import { onMounted, ref } from 'vue';


const usuarios = ref([])

async function buscarUsuarios(){
    const resposta = await fetch("https://jsonplaceholder.typicode.com/users")

    usuarios.value = await resposta.json()
}

onMounted(() => {
    buscarUsuarios()
})

</script>

<template>
    <section>
        <article v-for="usuario in usuarios" :key="usuario.id">
            <h3>Nome: {{ usuario.name }}</h3> 
            <p>Email: {{ usuario.email }}</p>
            <p>Cidade: {{ usuario.address.city }}</p>
        </article>
    </section>
</template>


<style scoped>
    section{
        display: flex;
        flex-wrap: wrap;
        gap: 20px;
        align-items: center;
        justify-content: center;
    }

    article{
        padding: 10px;
        background-color: rgba(0, 128, 0, 0.637);
        color: white;
        border: 2px solid black;
        border-radius: 10px;
        box-shadow: 0 10px 10px 0 black;
    }
</style>