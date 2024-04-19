<script setup>
import Question from '../components/Question.vue';
import QuizHeader from '../components/QuizHeader.vue';
import { useRoute } from 'vue-router';
import { ref, computed } from 'vue'
import quizes from '../data/quizes.json'
import Result from '../components/Result.vue'

const route = useRoute()
const quizId = parseInt(route.params.id);


const quiz = quizes.find(q => q.id === quizId);
const currentQuesionIndex = ref(0);
const numberOfCorrectAnswers = ref(0);
const showResult = ref(false);
const questionStatus = computed(() => `${currentQuesionIndex.value} / ${quiz.questions.length}`
)
const barPercentage = computed(() => `${currentQuesionIndex.value / quiz.questions.length * 100}%`
)
const onOptionSelected = (isCorrect) => {
  if (isCorrect) {
    numberOfCorrectAnswers.value++;
  }
  if (quiz.questions.length - 1 === currentQuesionIndex.value) {
    showResult.value = true
  }
  currentQuesionIndex.value++;
}
</script>

<template>
  <div>
    <QuizHeader :questionStatus="questionStatus" :barPercentage="barPercentage" />
    <div>
      <Question :question="quiz.questions[currentQuesionIndex]" @selectOption="onOptionSelected" v-if="!showResult" />
      <Result v-else :quizQuestionLength="quiz.questions.length" :numberOfCorrectAnswers="numberOfCorrectAnswers" />
    </div>

  </div>
</template>