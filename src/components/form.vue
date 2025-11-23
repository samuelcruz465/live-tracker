<template>
  <div class="box formulario">
    <div class="columns">
      <div
        class="column is-8"
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
        <UseTemporizador @ao-temporizador-finalizado="finalizarTarefa"/>
      </div>
    </div>
  </div>
</template>


<script lang="ts">
    import { defineComponent } from 'vue';
    import UseTemporizador from './temporizador.vue';

    export default defineComponent({
        name: 'UseForm',
        emits: ['aoSalvarTarefa'],
        components:{
            UseTemporizador,
        },
        data () {
            return {
                descricao: ''
            }
        },
        methods: {
            finalizarTarefa(timePlayed: number): void{
                this.$emit('aoSalvarTarefa', {
                    duracaoEmSegunds: timePlayed,
                    descricao: this.descricao
                }),
                console.log(timePlayed)
                console.log(this.descricao)
                this.descricao = ''
            }
        }
    })
</script>
<style>
    .formulario{
        color: var(--texto-primario);
        background-color: var(--bg-primario)
    }
</style>