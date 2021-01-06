<template>
    <div>
        <button :class="estiloDoBotao" class="botao" :type="tipo" @click="disparaAcao()">{{ rotulo }}</button>
    </div>
</template>

<script>

   
    export default {

        props: {
            tipo:{
                required:true,
                type: String
            },
            rotulo: {
                required: true,
                type: String
            },
            confirmacao: Boolean,
            estilo: String
        },

        methods: {
            disparaAcao(){
                if(this.confirmacao){
                    if(confirm('Confirma operação?')){
                        this.$emit('botaoAtivado');
                    }
                    return;
                }
                this.$emit('botaoAtivado')
            }
        },

        computed:{

            estiloDoBotao(){
                if(this.estilo =='padrao' || !this.estilo){
                    return 'botao-padrao'
                }
                if(this.estilo =='perigo'){
                    return 'botao-perigo'
                }
            }
        }
    }
</script>

<style scoped>
    .botao {
        display: inline-block;
        padding: 10px;
        border-radius: 3px;
        margin: 10px;
        font-size: 1.2rem;
    }

    .botao-perigo{
        background: firebrick;
        color: white;
    }

    .botao-padrao {
        background: darkcyan;
        color: white;
    }
</style>