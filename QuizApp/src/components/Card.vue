<script setup>
import { defineProps } from 'vue';
    const props = defineProps(['quiz'])
</script>
<template>
     <div  class="card">
        <img :src="quiz.img" alt="quiz-image">
        <div class="card-text">
          <h2>{{ quiz.name }}</h2>
          <p>{{ quiz.questions.length }} Questions</p>
        </div>
      </div>
</template>
<style scoped>
.card{
  width: 310px;
  overflow: hidden;
  box-shadow: 1px 1px 10px rgba(0,0,0,01);
  cursor: pointer;
  border-radius: 2%;
  margin: 25px 0 30px 0;

}
.card img {
  width: 100%;
  height: 190px;
  margin: 0;
}
.card .card-text{
  padding: 0 5px;
}
.card .card-text h2{
font-weight: bold;
}
</style>