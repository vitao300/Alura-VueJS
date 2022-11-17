<template>
  <main class="columns is-galpless is-multiline" :class="{ 'modo-escuro': modoEscuro }">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema" />
    </div>
    <div class="column is-three-quarter conteudo">
      <FormularioComponent @aoSalvarTarefa="salvarTarefa" />
      <div class="lista">
        <TarefaComponent v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />
        <BoxComponent v-if="listaEstaVazia">
          Você ainda não iniciou nenhuma tarefa!
        </BoxComponent>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import FormularioComponent from './components/Formulario.vue';
import TarefaComponent from './components/Tarefa.vue';
import ITarefa from './interfaces/ITarefa'
import BoxComponent from './components/Box.vue';


export default defineComponent({
  name: "App",
  components: { BarraLateral, FormularioComponent, TarefaComponent, BoxComponent },
  data() {
    return {
      tarefas: [] as ITarefa[],
      modoEscuro: false
    }
  },
  computed: {
    listaEstaVazia(): boolean {
      return this.tarefas.length === 0;
    }
  },
  methods: {
    salvarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa);
    },
    trocarTema(modoEscuro: boolean) {
      this.modoEscuro = modoEscuro;
    }
  }
});
</script>

<style>
.lista {
  padding: 1.25rem;
}

main {
  --bg-primario: #FFF;
  --texto-primario: #000;
}

main.modo-escuro {
  --bg-primario: #2b2d42;
  --texto-primario: rgb(134, 24, 24);
}

.conteudo {
  background-color: var(--bg-primario);
}
</style>
