<template>
<main class="columns is gapless is-multiline " :class="{'modo-escuro': modoEscuroAtivo}">
  <div class="column is-one-quarter">
    <SideBar @ao-tema-alterado="trocarTema"/>
    
  </div>

   <div class="column is-three-quarter conteudo">
    <FormsTask  @aoSalvarTarefa = "salvarTarefa"/>
    <div class="Lista">
      <TarefaForms v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
    </div>
    <BoxMessageComp v-if="listaEstaVazia">
      Você não realizou nenhuma tarefa por enquanto 
    </BoxMessageComp>
   </div>

</main>
</template>

<script lang="ts">

import { defineComponent } from 'vue';
import SideBar from './components/SideBar.vue'
import FormsTask from './components/FormsTask.vue'
import TarefaForms from './components/TarefaForms.vue';
import ITarefa from './interfaces/ITarefa';
import BoxMessageComp from './components/BoxMessageComp.vue';
export default defineComponent({
  name: 'App',
  components: {
    SideBar, 
    FormsTask,
    TarefaForms,
    BoxMessageComp
  },

  data(){
    return{
      tarefas: [] as ITarefa[],
      modoEscuroAtivo: false
    }
  },

  computed: {
    listaEstaVazia() : boolean {
      return this.tarefas.length === 0
    }
  },

  methods:{
    salvarTarefa( tarefa: ITarefa){
      this.tarefas.push(tarefa)
    },
    trocarTema (modoEscuroAtivo: boolean){
      this.modoEscuroAtivo = modoEscuroAtivo
    }
  }

});
</script>

<style>
    .lista{
        padding: 1.25rem;
    }

    
    body, input, textarea, select, button, strong, .has-text-weight-bold {
        color: var(--texto-primario) !important;
    }

    main{
        --bg-primario: #fde56b;
        --box: #5a75fd;
        --texto-primario: #fff; 
        --button-input-background: #2A3C97; 
    }

    main.modo-escuro{
        --bg-primario: #0C112C;
        --box: #fde56b;
        --texto-primario: #0C112C; 
        --button-input-background: #BAA228; 
    }

    input::placeholder,
    textarea::placeholder {
        color: var(--texto-primario) !important;
        opacity: 1; 
    }

    .box{
        
        background-color: var(--box) !important;
        margin: 2em 3em 0 3em !important;
    }

    .button, .input{
        
        background-color: var(--button-input-background) !important;
    }

    .conteudo{
        background-color: var(--bg-primario);
    }

</style>
