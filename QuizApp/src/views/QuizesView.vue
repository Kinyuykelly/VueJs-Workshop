<script setup>
import { ref, watch } from 'vue';
import q from '../data/quizes.json';
import Card from '../components/Card.vue';


const quizes = ref(q);
const search = ref('');

watch(search, () => {
  quizes.value = q.filter(
    quiz => quiz.name.toLowerCase().includes(search.value.toLowerCase())
  )
})
</script>

<template>
  <header>
    <h1>Quizes</h1>
    <input v-model.trim="search" type="text" placeholder="Search...">
  </header>
  <div class="options-container">
    <Card v-for="quiz in quizes" :quiz="quiz" />

  </div>
</template>
<style scoped>
header {
  margin: 10px 0 30px 0;
  display: flex;
  align-items: center;
}

header h1 {
  font-weight: bold;
  margin-right: 30px;
}

header input {
  border: none;
  background: rgba(123, 128, 128, 0.1);
  padding: 10px;
  border-radius: 5px;
  height: 25px;
  width: 600px;
}

.options-container {
  display: flex;
  flex-wrap: wrap;
  margin-top: 40px;
  gap: 30px;
}
</style>
