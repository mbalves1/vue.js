<template>
  <div>
    <h1 class="centralizado"> {{titulo}} </h1>

    <input tyope="search" class="filtro" v-on:input="filtro = $event.target.value" placeholder="filtre pelo titulo">
    {{filtro}}
    <ul class="listaFotos">
      <li class="listaFotosItem" v-for="foto of fotosComFiltro">

        <meuPainel :titulo="foto.titulo">
          <imagem-responsiva :url="foto.url" :titulo="foto.titulo" />
          <meu-botao 
            tipo="button" 
            rotulo="Remover" 
            @botaoAtivado="remove(foto)"
            :confirmacao="true"
            estilo="perigo" />
        </meuPainel>

      </li>
    </ul>

  </div>
</template>

<script>
import Painel from '../shared/painel/Painel.vue'
import ImagemResponsiva from '../shared/imagem-responsiva/imagemResponsiva.vue'
import Botao from '../shared/botao/botao.vue'

export default {

  components: {
    'meuPainel': Painel,
    'ImagemResponsiva': ImagemResponsiva,
    'meu-botao': Botao
  },

  data(){
    return {
      titulo:"App Pictures",
      fotos: [],
      filtro: ''
    }
  },

  computed: {

    fotosComFiltro(){
      if(this.filtro){
        let exp = new RegExp(this.filtro.trim(), 'i')
        return this.fotos.filter(foto => exp.test(foto.titulo))
      } else {
        return this.fotos
      }
    }
  },

  methods: {

    remove(foto){
    
        alert('removeu marmota ' + foto.titulo)
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
  
  .centralizado{
    text-align: center;
  }

  .listaFotos{
    list-style: none;
  }

  .listaFotos .listaFotosItem{
    display: inline-block;
  }

  

   
</style>
