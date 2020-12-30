<template>
  <div>
    <h1> {{titulo}} </h1>

    <ul>
      <li v-for="foto of fotos">
        <img :src="foto.url" :alt="foto.titulo">
      </li>
    </ul>

  </div>
</template>

<script>
export default {
  data(){
    return {
      titulo:"App Pictures",
      fotos: [
        {
          url: 'https://matsudapet.com.br/blog/wp-content/uploads/2019/08/shutterstock_559799125-compressed.jpg',
          titulo: 'cachorro'
        },
        {
          url: 'https://matsudapet.com.br/blog/wp-content/uploads/2019/08/shutterstock_559799125-compressed.jpg',
          titulo: 'cachorrão'
        }
      ]
    }
  }
}
</script>

<style>
</style>
