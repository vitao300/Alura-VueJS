<template>
    <BoxComponent>
        <div class="columns">
            <div class="column id-7">
                {{tarefa.descricao || 'Tarefa sem descrição'}}
            </div>
            <div class="column">
                <CronometroComponent :tempo-em-segundos="tarefa.duracaoEmSegundos" />
            </div>
        </div>
    </BoxComponent>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import CronometroComponent from './Cronometro.vue';
import ITarefa from '../interfaces/ITarefa';
import BoxComponent from './Box.vue';

export default defineComponent({
    name: 'TarefaComponent',
    components: {
        CronometroComponent,
        BoxComponent
    },
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    }
});

</script>
