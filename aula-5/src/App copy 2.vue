<template>
  <div v-if="status == 'carregando'">
    <h1>Teste</h1>
    <p>AJDSADALKDJALKDJA</p>
    <a href="www.google.com.br">Google</a>
    o conteúdo está sendo carregado...
    <button v-if='exibeBotao' >Clique em mim!!!</button>
  </div>
  <div v-else-if="status == 'erro'">
    houve um erro ao carregar as informações...
  </div>
  <div v-else>
    aqui está sua lista de informações!
  </div>
</template>

<script setup>
import { ref } from 'vue';

const status = ref('erro');
const exibeBotao = ref(true);
</script>