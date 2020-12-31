<template>
  <div  class="corpo">
    <h1 class="centralizado"> {{titulo}} </h1>

    <ul class="listaFotos">
      <li class="listaFotosItem" v-for="foto of fotos">

        <meuPainel :titulo="foto.titulo">
           <img class="imagemResponsiva" :src="foto.url" :alt="foto.titulo">
        </meuPainel>

      </li>
    </ul>

  </div>
</template>

<script>
import Painel from './components/shared/painel/Painel.vue'

export default {

  components: {
    'meuPainel': Painel
  },

  data(){
    return {
      titulo:"App Pictures",
      fotos: []
    }
  },

  created(){
    let promise = this.$http.get('http://localhost:3000/v1/fotos')
    promise
      .then(res => res.json())
      .then(fotos => this.fotos = fotos, err => console.log(err))
  }
}
</script>

<style>
  .corpo{
    font-family: Helvetica, sans-serif;
    width: 96%;
    margin: 0 auto;
  }

  .centralizado{
    text-align: center;
  }

  .listaFotos{
    list-style: none;
  }

  .listaFotos .listaFotosItem{
    display: inline-block;
  }

  .imagemResponsiva{
    width: 100%;
  }
  

   
</style>
