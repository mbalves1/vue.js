<template>
        <div class="painel">
          <h2 class="painelTitulo" @dblclick="visivel = !visivel" >{{ titulo }}</h2>
          <transition name="painel-fade">
            <div class="painelConteudo" v-show="visivel">
              <slot></slot>
            </div>
          </transition>
        </div>
</template>

// v-on: > @

<script>
export default {
    props: ['titulo'],

    data() {

      return {
        visivel:"true"
      }
    }
}
</script>

<style scoped>
  
  /* Estilo painel */
  .painel {
    padding: 0 auto;
    border: solid 2px grey;
    display: inline-block;
    margin: 5px;
    box-shadow: 5px 5px 10px grey;
    width: 200px;
    height: 100%;
    vertical-align: top;
    text-align: center;
  }

  .painel .painelTitulo {
    text-align: center;
    border: solid 2px;
    background: lightblue;
    margin: 0 0 15px 0;
    padding: 10px;
    text-transform: uppercase;
  }

  * {
      box-shadow: 5px 5px 5px black;
  }

  h2 {
    cursor: pointer;
  }

  .painel-fade-enter,
  .painel-fade-leave-active {
    opacity: 0;
  }

  .painel-fade-enter-active,
  .painel-fade-leave-active {
    transition: opacity .4s;
  }


</style>
