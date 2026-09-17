<template>
  <div class="card" :style="`background-color: ${color}`">
    <div>{{ title }}</div>
    <h2>{{ value }}</h2>
    <button v-if="mostraBotao" @click="emit('clicoulaele', title)">
      Esclói
    </button>
  </div>
</template>

<script setup>
const props = defineProps({
  title: {
    type: String,
    default: '',
  },
  color: {
    type: String,
    default: 'pink',
  },
  value: {
    type: Number,
    default: 0,
  },
  mostraBotao: {
    type: Boolean,
    default: false,
  },
});

const emit = defineEmits(['clicoulaele']);
</script>

<style scoped>
.card {
  border: 2px solid black;
  border-radius: 4px;
  padding: 10px;
  margin: 10px;
  color: white;
}
</style>
