<template>
    <BoxMessageComp>
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao || 'Tarefa sem descrição' }}
            </div>
            <div class="column">
                <CronometroForms :tempoEmSegundos="tarefa.duracaoEmSegudos"/>
            </div>
        </div>
    </BoxMessageComp>
</template>

<script lang="ts">
import { defineComponent, Prop, PropType } from 'vue'
import CronometroForms from './CronometroForms.vue';
import ITarefa from '@/interfaces/ITarefa';
import BoxMessageComp from './BoxMessageComp.vue';

export default defineComponent({
    name: 'TarefaForms',
    components: {
        CronometroForms,
        BoxMessageComp
    },

    props:{
        tarefa:{
            type: Object as PropType<ITarefa>,
            required: true
        }
    }
})

</script>
