<template>
  <ul>
    <li v-for='(fruta, i) in frutas' :key='i'>
      {{ fruta.nome }} custa R$ {{ fruta.preco.toFixed(2) }}
    </li>
    <hr>
    <table>
      <tr>
        <th>Código</th>
        <th>Nome</th>
        <th>Nota</th>
      </tr>
      <tbody>
        <tr v-for="aluno in alunos" :key='aluno.codigo'>
          <td>{{aluno.codigo}}</td>
          <td>{{aluno.nome}}</td>
          <td>{{aluno.nota}}</td>
        </tr>
      </tbody>
    </table>
    <hr>
    <div v-for="numero in qtd" :key='numero'>
      {{ numero }}
    </div>
  </ul>
</template>

<script setup>
import { ref } from 'vue';

const frutas = ref([
  { nome: 'banana', preco: 2.00 },
  { nome: 'maça', preco: 3.00 },
  { nome: 'manga', preco: 9.00 },
  { nome: 'uva', preco: 27.00 },
]);

const alunos = ref([
  { codigo: 1, nome: 'Ruan', nota: 9.00 },
  { codigo: 2, nome: 'Raphael', nota: 8.00 },
  { codigo: 29, nome: 'Moto', nota: 3.00 },
  { codigo: 727381, nome: 'Arnecke', nota: 6.00 },
])

const qtd = ref(291)

</script>

<style scoped>
table, tr, th, td {
  border: 1px solid;
  border-collapse: collapse;
}

</style>