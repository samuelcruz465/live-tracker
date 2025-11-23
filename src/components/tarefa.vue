<template>
    <UseBox>
        <div class="column">
            <div class="column is-7">
                {{ tarefa.descricao || 'Tarefa sem nome' }}
            </div>
            <div class="column">
                <UseCronometer :time-secs="tarefa.duracaoEmsecs" />
            </div>
        </div>
    </UseBox>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import UseCronometer from './cronometer.vue';
import ITarefa from '../interfaces/ITarefa';
import UseBox from './box.vue';
export default defineComponent({
    name: 'UseTarefa',
    components: {
        UseCronometer,
        UseBox,
    },
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        },
    },
});

</script>
