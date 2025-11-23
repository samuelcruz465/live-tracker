<template>
    <section>
        <strong class="display">
            {{ timePlayed }}
        </strong>
    </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'UseCronometer',
    //compontente filho

    //propriedade
    props: {
        timeSecs:{
            type: Number,
            default: 0,
        }
    },
    computed: {
        timePlayed(): string {
            return new Date(this.timeSecs * 1000).toISOString().substr(11, 8)
        }
    },
})
</script>

<style scoped>
    .display{
        color: var(--texto-primario)
    }
</style>