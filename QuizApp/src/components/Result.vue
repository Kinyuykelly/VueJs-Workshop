<script setup>
import { defineProps } from 'vue';
import {RouterLink} from 'vue-router'

const { quizQuestionLength, numberOfCorrectAnswers} = defineProps(['quizQuestionLength', 'numberOfCorrectAnswers'])
</script>


<template>
    <div class="results">
        
        <p>Your Results...</p>
      <h1>
         {{ numberOfCorrectAnswers }} / {{ quizQuestionLength }}
         
      </h1>
      <RouterLink  class="active-link" to="/">
        Go back Home
      </RouterLink>
    </div>
</template>

<style scoped>
.results{
text-align: center;
padding: 100px 0;
}
p{
    font-style: 25px;
   
}
h1{
    font-size: 80px;
}
.active-link{
    color: rgb(60, 55, 161);
    background-color: white;
    font-weight: bold;
    font-size: larger;
}
</style>