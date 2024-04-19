<script setup>
import { defineProps, defineEmits } from 'vue';
const { question } = defineProps(['question'])

const emit = defineEmits('selectOption');
const emitSelectedOption = (isCorrect) => {
    emit('selectOption', isCorrect)
}
</script>

<template>
    <div>
        <div class="question-container">
            <h1 class="question">{{ question.text }}</h1>
        </div>

        <div class="options-container">
            <div class="option" @click="emitSelectedOption(option.isCorrect)" v-for="option in question.options"
                :key="option.id">
                <p class="option-label">{{ option.label }}</p>
                <p class="option-value">{{ option.text }}</p>
            </div>
        </div>
    </div>

</template>
<style scoped>
.question-container {
    margin-top: 20px;

}

.question {
    font-size: 40px;
    margin-bottom: 20px;
}

.option {
    display: flex;
    margin-bottom: 20px;
    cursor: pointer;
}

.option-label {
    background-color: rgb(60, 55, 161);
    height: 50px;
    width: 50px;
    font-style: 30px;
    display: flex;
    align-items: center;
    justify-content: center;
}

.option-value {
    display: flex;
    background-color: rgb(242, 239, 239);
    width: 100%;
    font-style: 30px;
    align-items: center;
    padding-left: 20px;
}
</style>