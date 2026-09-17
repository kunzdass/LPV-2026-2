<template>
  <div>
    <input
      placeholder='Tarefa'
      v-model="inputTarefa"
      @keyup.enter='adicionarTarefa'
    >
    <button @click='adicionarTarefa'>+</button>
    <hr>
    <input type="checkbox" @click='marcarTodas'> Marcar tudo como lido
    <ul>
      <li v-for="(tarefa, index) in tarefas" :key='index'
          :class="{
            'texto-riscado': tarefa.feito
          }">
        <input
          type="checkbox"
          v-model="tarefa.feito"
        >
        {{ tarefa.nome }}
        <button @click='excluirTarefa(index)'>Excluir</button>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref } from 'vue';
const inputTarefa = ref('');
const tarefas = ref([]);

function adicionarTarefa () {
  if (!inputTarefa.value.trim()) {
    return alert('Informe a tarefa')
  }

  const novaTarefa = {
    nome: inputTarefa.value,
    feito: false
  }

  tarefas.value.push(novaTarefa);
  inputTarefa.value = '';
}

function excluirTarefa (indexParaExclusao) {
  tarefas.value.splice(indexParaExclusao, 1)
}

function marcarTodas () {
  tarefas.value.forEach(tarefa => tarefa.feito = true)
}
</script>

<style scoped>
.texto-riscado {
  text-decoration: line-through;
}
</style>
