<template>
  <h1>Lista de Cards</h1>
  <div class="lista">
    <div v-for="indicador in indicadores" :key="indicador.titulo" class="card">
      <Card
        :title="indicador.titulo"
        :color="indicador.cor"
        :value="indicador.valor"
        mostra-botao
        @clicoulaele="clicadaNoCardIndicadores"
      ></Card>
    </div>
  </div>
  <div class="lista">
    <div v-for="nota in notas" :key="nota.aluno" class="card">
      <Card
        :title="nota.aluno"
        :color="nota.nota < 5 ? 'red' : nota.nota < 7 ? 'orange' : 'green'"
        :value="nota.nota"
      ></Card>
    </div>
  </div>
  <div class="lista">
    <div v-for="(recurso, i) in recursos" :key="i" class="card">
      <Card :title="recurso"></Card>
    </div>
  </div>
</template>

<script setup>
import Card from './components/Card.vue';
import { onMounted, ref } from 'vue';
import axios from 'axios';
const indicadores = ref([
  { titulo: 'a receber', cor: 'grey', valor: 2 },
  { titulo: 'a pagar', cor: 'blue', valor: 14 },
  { titulo: 'pagas', cor: 'green', valor: 96 },
  { titulo: 'vencidas', cor: 'red', valor: 632 },
]);

const notas = ref([
  { aluno: 'Fulano', nota: 8 },
  { aluno: 'Ciclano', nota: 6.5 },
  { aluno: 'Beltrano', nota: 3 },
  { aluno: 'Erivelton', nota: 10 },
]);

const recursos = ref([]);

onMounted(() => {
  obterDados();
});

async function obterDados() {
  const resposta = await axios.get('https://api-lpv.onrender.com/');
  recursos.value = resposta.data.recursos;
}

function clicadaNoCardIndicadores(tituloQueClicamos) {
  const index = indicadores.value.findIndex((el) => {
    return el.titulo == tituloQueClicamos;
  });
  indicadores.value.splice(index, 1);
}
</script>

<style scoped>
.lista {
  height: 200px;
  width: 95%;
  border: 5px dotted blue;
  margin: 10px;
  display: flex;
}

.card {
  width: 55%;
}
</style>
