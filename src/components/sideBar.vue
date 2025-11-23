<template>
    <header>
        <h1>
            <!--adiciona imagem no header-->
            <img src="../assets/logo.png" alt="">
        </h1>
        <button class="button" @click="alterarTema">
            {{ ButtonText }}
        </button>
    </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    //nome do componente para exportar
    name: 'SideBar',
    emits:['aoTemaAlterado'],
    data () {
        return {
            darkMode: false,
        }
    },
    computed:{
        ButtonText () {
            if(this.darkMode){
                return 'Desativar modo escuro'
            } else {
                return 'Ativar modo escuro'
            }
        }
    },
        methods: {
        alterarTema() {
            this.darkMode = !this.darkMode
            this.$emit('aoTemaAlterado', this.darkMode)
        }
    }
})
</script>

<style scoped>
/*todo o estilo do componente*/
header {
    text-align: center;
    padding: 1rem;
    background: #0d3b66;
    width: 100%;
    height: 100vh;
}

@media only screen and (max-width: 768px) {
    header {
        padding: 2.5rem;
        height: auto;
    }
}
</style>