<script setup>
// Importações Sempre Primeiro;
import { reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue';
import Formulario from './components/Formulario.vue';
import ListaDeTarefas from './components/ListaDeTarefas.vue';

  const estados = reactive({
    filtro: 'todas',
    tarefaTemp: '',
    tarefas: [
      {
        titulo: 'Estudar ES6',
        finalizada: false,
      },
      {
        titulo: 'Estudar VueJS',
        finalizada: true,
      },
      {
        titulo: 'Tomar Água',
        finalizada: true,
      }
    ]
  })

  const getTarefasPendentes = () => {
    return estados.tarefas.filter(tarefa => !tarefa.finalizada);
  }

  const getTarefasFinalizadas = () => {
    return estados.tarefas.filter(tarefa => tarefa.finalizada);
  }

  const getTarefasFiltradas = () => {
    // Utilizando Desestruturação;
    const { filtro } = estados;

    // O "Switch" é Como Vários "if"s;
    switch (filtro) {
      case 'pendentes':
        return getTarefasPendentes();
      case 'finalizadas':
        return getTarefasFinalizadas();
      default:
        return estados.tarefas;
    }
  }

  const cadastraTarefa = () => {
    const tarefaNova = {
      titulo: estados.tarefaTemp,
      finalizada: false,
    }
    estados.tarefas.push(tarefaNova);
    estados.tarefaTemp = '';
  }
</script>

<template>
  <div class="container">
    <Cabecalho :tarefas-pendentes="getTarefasPendentes().length"/>
    <Formulario :trocar-filtro="evento => estados.filtro = evento.target.value" :tarefa-temp="estados.tarefaTemp" :edita-tarefa-temp="evento => estados.tarefaTemp = evento.target.value" :cadastra-tarefa="cadastraTarefa" />
    <ListaDeTarefas :tarefas-pendentes="getTarefasPendentes().length" :tarefas="getTarefasFiltradas()" />
  </div>
</template>