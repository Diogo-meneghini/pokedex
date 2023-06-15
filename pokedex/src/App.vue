<script setup>
  import Header from './components/Header.vue'
  import Card from './components/Card.vue'
  import { ref } from 'vue'
 
  const numbers = Array.from({ length: 50 }, (_, index) => index + 1);

  const valorEmitido = ref('')

  defineEmits(['pesq'])
  const handlePesquisar = (valor) =>{
    valorEmitido.value = valor
  }
</script>

<template>
    <Header @pesq="handlePesquisar" class="header"></Header>
    <div class="cards-container">
      <div v-if="valorEmitido" class="cards">
        <Card :indice="valorEmitido"></Card>
      </div>
      <div v-else class="cards" v-for="number in numbers" :key="number">
        <Card :indice="number"></Card>
      </div>
    </div>

</template>

<style>
    .cards-container{
      display: flex;
      justify-content: center;
      align-items: center;
      flex-wrap: wrap;
    }
    .cards{
      display: flex;

    }
    #app{
      display: flex;
      align-items: center;
      flex-direction: column;
    }
</style>
