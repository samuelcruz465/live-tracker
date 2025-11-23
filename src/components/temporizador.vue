<template>
        <div
          class="is-flex is-align-items-center is-justify-content-space-between"
        >
        <!---->
        <UseCronometer :timeSecs="timeSecs" />
          <button class="button" @click="iniciar" :disabled="cronometerRunning">
            <span class="icon">
              <i class="fas fa-play"></i>
            </span>
            <span>play</span>
          </button>
          <button class="button" @click="parar" :disabled="!cronometerRunning">
            <span class="icon">
              <i class="fas fa-stop"></i>
            </span>
            <span>stop</span>
          </button>
        </div>
</template>

<script lang="ts">
    import { defineComponent } from 'vue';
    import UseCronometer from './cronometer.vue';

    export default defineComponent({
        name: 'UseTemporizador',
        emits:['aoTemporizadorFinalizado'],
        components:{
            UseCronometer
        },
        //define o contador = 0
        data(){
            return {
                timeSecs: 0,
                cronometer: 0,
                cronometerRunning: false,
            }
        },

        //métodos
        methods: {
            //inicia a contagem
            iniciar(){
              this.cronometerRunning = true
              this.cronometer = setInterval(() => {
                    this.timeSecs += 1
                }, 1000)
              
            },
            //para o contador
            parar(){
              this.cronometerRunning = false
                clearInterval(this.cronometer)
                //grava evento ao parar cronometro
                this.$emit('aoTemporizadorFinalizado', this.timeSecs)
                this.timeSecs = 0
            }
        }
    })
</script>
