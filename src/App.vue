<template>
  <main class="columns is-gapless is-multiline" :class="{'dark-mode': darkModeActive}">
    <div class="coluns is-one-quarter">
      <!-- chama o componente .vue-->
      <SideBar @ao-tema-alterado="trocarTema" />

    </div>
    <div class="coluns is-three-quarter conteudo">
      <!--chama o formulário-->
      <UseForm @aoSalvarTarefa="salvarTarefas" />
      <!--lista de tarefas-->
      <div class="lista">
        <UseTarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />

      </div>
      <UseBox v-if="emptyList">
        Suas tarefas estão vazias! Iniicie uma nova tarefa acima.
      </UseBox>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
//import component
import SideBar from './components/sideBar.vue'
import UseForm from './components/form.vue';
import UseTarefa from './components/tarefa.vue';
import ITarefa from './interfaces/ITarefa';
import UseBox from './components/box.vue'
export default defineComponent({
  name: 'App',
  //nomeia o componente a ser chamado acima
  components: {
    SideBar,
    UseForm,
    UseTarefa,
    UseBox,
  },

  data() {
    return {
      tarefas: [] as ITarefa[],
      darkModeActive: false,
    }
  },

  computed: {
    emptyList(): boolean {
      return this.tarefas.length === 0;
    }
  },

  methods: {
    salvarTarefas(tarefa: ITarefa) {
      this.tarefas.push(tarefa)
    },
    trocarTema(darkModeActive: boolean) {
      this.darkModeActive = darkModeActive
    },

  },


});
</script>

<style>
.lista {
  padding: 1.25rem;
}

main {
  --bg-primario: #fff;
  --texto-primario: #000;

}

main.dark-mode {
  --bg-primario: #2a2a2a;
  --texto-primario: #ddd;
}

.conteudo {
  background-color: var(--bg-primario);
}
</style>
