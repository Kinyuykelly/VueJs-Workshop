<script setup>
import { ref } from 'vue';
const showModal = ref(false)
const newNote = ref("")
const notes = ref([])
const errorMessage = ref("");

function  getRandomColor() {
  return "hsl(" + Math.random() * 360 +", 100%, 75%)";

}

const AddNote = () =>{
  if (newNote.value.length < 10){
   return errorMessage.value = "Note needs to be ten characters or more"
  }
  notes.value.push({
    id: Math.floor(Math.random() * (1000000)),
    text: newNote.value,
    date: new Date(),
    backgroundColor: getRandomColor()
  })
  showModal.value = false
  newNote.value = ""
  errorMessage.value = ""
}

</script>
<template>
  <main>
    <div v-if="showModal" class="overlay">
      <div class="modal">
        <textarea v-model.trim="newNote" name="note" id="note" cols="30" rows="10" ></textarea>
        <p v-if="errorMessage">{{ errorMessage }}</p>
       <div class="buttons">
        <button class="btn" @click="AddNote">Add Note</button>
      <button class="btn" @click="showModal = false">Close</button>
       </div>
    </div>
    </div>
    
    <div class="container">
      <header>
        <h1>Notes</h1>
      <button @click="showModal = true">+</button>
      </header>
      <div class="cards-container">
        <div v-for="note in notes" :key="{id: note.id}" class="card" :style="{backgroundColor: note.backgroundColor}">
          <p class="main-text">{{ note.text }}</p>
          <p class="date">{{ note.date.toLocaleDateString()}}</p>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
  main{
    height: 100vh;
    width: 100vw;
  }
  .container{
    max-width: 1000px;
    padding: 10px;
    margin: auto

  }
  header{
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  h1{
    font-weight: bold;
    margin-bottom: 25px;
    font-size: 75px;
  }
  .cards-container{
    display: flex;
    flex-wrap: wrap;
  }
  header button{
    border: none;
    padding: 10px;
    width: 50px;
    height: 50px;
    cursor: pointer;
    background-color: rgb(21, 22, 21);
    color: white;
    font-size: 20px;
    border-radius: 50%;
  }
  .card{
    width: 225px;
    height: 225px;
    background-color: rgb(235, 193, 138);
    padding: 15px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    margin-right: 20px;
    margin-bottom: 20px;
    border-radius: 10px;
    word-wrap: break-word;
    
  }
  .date{
    font-size: 12.5px;
    font-weight: bold;
  }
  .overlay{
    position: absolute;
    width: 100%;
    height: 100%;
    background-color: rgba(0,0,0,0.77);
    z-index: 10;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .modal{
    width: 750px;
    background-color: white;
    border-radius: 10px;
    padding: 30px;
    display: flex;
    flex-direction: column;
    padding: 30px;
  }
  .buttons{
    display: flex;
    gap: 30px;
    justify-content: left;
    padding-top: 20px;
  }.modal textarea{
    border: 1px solid #54535322;
    border-radius: 10px;
  }
  .modal textarea:focus{
    outline:1px solid #5f1b6f;
  }

  .modal button:nth-child(2){
    width: 25%;
    height: 50px;
    border: none;
    font-size: 18px;
    border-radius: 15px;
    cursor: pointer;
    background-color: #958d8e;
    color: #fff;
    transition: 125ms ease-in;

  }
  .modal button:nth-child(1){
    padding: 10px 20px;
    width: 25%;
    height: 50px;
    border: none;
    font-size: 18px;
    border-radius: 15px;
    cursor: pointer;
    background-color: #5f1b6f;
    color: #fff;
    transition: 125ms ease-in;

  }
  .modal button:hover{
    opacity: 0.8;
  }
  .modal p{
    color: red;
  }
</style>