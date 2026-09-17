<template>
  <div>
    <h2>Cálculo de média</h2>
    <input
      v-model="primeiraNota"
      :placeholder="help"
    ><br>
    <input
      v-model="segundaNota"
      :placeholder="help"
      @keyup='tratarTeclada'
    ><br>
    <br>
    <button
      :disabled='desabilitarBotao'
      @click='calcularMedia'
    >
      Calcular Média
    </button>
    <div v-if="media">
      A média é: {{ media }}<br>
      O aluno está: {{ situacao }}
    </div>
    <hr>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const primeiraNota = ref(null);
const segundaNota = ref(null);
const media = ref(null);

const desabilitarBotao = computed(() => {
  return !Number(primeiraNota.value) || !Number(segundaNota.value);
});

const help = computed(() => {
  if (!Number(primeiraNota.value) && !Number(segundaNota.value)) {
    return 'Informe as duas notas para calcular a média';
  } else if (!Number(primeiraNota.value) && Number(segundaNota.value)) {
    return 'Falta informar a primeira nota';
  } else if (Number(primeiraNota.value) && !Number(segundaNota.value)) {
    return 'Falta informar a segunda nota';
  } else {
    return 'Tudo certo, clique em calcular';
  }
});

const situacao = computed(() => {
  return media.value >= 7
    ? 'Aprovado'
    : media.value < 7 && media.value >= 5
      ? 'Exame'
      : 'Reprovado';
});

function calcularMedia () {
  const n1 = Number(primeiraNota.value);
  const n2 = Number(segundaNota.value);
  media.value = (n1 + n2) / 2;
}

</script>