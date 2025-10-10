<template>
    <header>
        <h1>
            <img src="../assets/logo.png" alt="">
        </h1>

        <button class="button" @click="alterarTema">
            {{ textoBtn }}
        </button>
    </header>
</template>

<script lang="ts">
    import{ defineComponent } from 'vue'

    export default defineComponent({
        name: 'SideBar',
        emits: ['aoTemaAlterado'],
        data() {
            return{
                modoEscuroAtivo:false
            }
        },

        computed:{
            textoBtn (){
                if(this.modoEscuroAtivo){
                    return 'Desativar modo escuro'
                }

                return 'Ativar modo escuro'
            }
        },
        methods:{
            alterarTema(){
                this.modoEscuroAtivo = !this.modoEscuroAtivo
                this.$emit('aoTemaAlterado', this.modoEscuroAtivo)
            }
        }
    })

</script>

<style scoped>
    header{
        padding:1rem;
        background: url(../assets/background.jpg);
        width: 100%;
        height: 100vh;
        text-align: center;
    }

    h1 img{
        width: 50%;
        height: 50%;
    }

    @media only screen and(max-width: 768px){
        header{
            padding: 2.5rem;
            height: auto;
        }
    }

</style>