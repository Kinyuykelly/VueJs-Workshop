
<script setup> 
import { ref } from "vue"

let count = ref(0);
 const addToCount = () => {
  count.value = count.value + 1;
 }
 const subtractFromCount = () => {
  count.value = count.value - 1;
 }
</script>

<template>
  <main>
    <div>
      <h4>The count is ...</h4>
      <h1>{{ count }}</h1>
      <button @click="subtractFromCount()">-</button>
      <button @click="addToCount()">+</button>
    </div>
  </main>
</template>

<style scoped>
main{
  background: aliceblue;
  height: 100vh;
  height: 100vw;
  display: flex;
  align-items: center;
  justify-content: center;
}
div{
  text-align: center;
}
</style>