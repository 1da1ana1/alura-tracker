<template>
    <div class="box formulario">
        <div class="columns">
            <div class="column is-8" 
            role="form" 
            aria-label="Formulário para criação de uma nova tarefa"
            >
                <input 
                type="text" 
                class="input" 
                placeholder="Qual tarefa você deseja iniciar?"
                v-model="descricao"
                />
            </div>
            
             <div class="column">
                <TemporizadorForms @aoTemporizadorFinalizado="finalizarTarefa" />
             </div>
            
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import TemporizadorForms from './TemporizadorForms.vue';
export default defineComponent({
    name:"FormsTask",
    emits: ['aoSalvarTarefa'],
    components:{
        TemporizadorForms
    },

    data(){
        return {
            descricao: ''
        }
    },

    methods:{
        finalizarTarefa (tempoDecorrido: number) : void{
                        console.log('--- TESTE DE COMUNICAÇÃO ---');
            console.log('Componente FormsTask recebeu o evento para finalizar a tarefa!');
            console.log('Descrição que será salva:', this.descricao);
            this.$emit('aoSalvarTarefa',{
                duracaoEmSegundos: tempoDecorrido,
                descricao: this.descricao
            })
            this.descricao=''
        }
    }

})
</script>

<style>
    .formulario{
        color: var(--texto-primario);
        background-color: (--bg-primario);
    }
</style>