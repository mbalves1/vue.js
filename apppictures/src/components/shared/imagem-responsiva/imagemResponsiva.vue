<template>
     <img class="imagemResponsiva" :src="url" :alt="titulo">
</template>

<script>

export default {

    props: ['url', 'titulo']
}
</script>

<style scoped>

    .imagemResponsiva{
        width: 100%;
    }
  
</style>