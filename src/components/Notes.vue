<script setup>
import {ref} from 'vue';

const showModel = ref(false)
const newNote = ref(" ")
const errorMsg = ref(false)
const notes = ref([])
function getRandomColor() {
 return  "hsl(" + Math.random() * 360 + ", 100%, 75%)";
}

const addNote = ()=>{
  if (newNote.value.length <10){
    errorMsg.value = true
}
else{
  notes.value.push({
    id:notes.value.length,
    text:newNote.value,
    date:new Date(),
    backgroundcolor :getRandomColor()
  })
  showModel.value = false  //after adding the note we dont need to display the model box
  //setting the text area state to null
  newNote.value=" "
  errorMsg.value = false

}
  }


const deleteNote = (noteId) => {
  const index = notes.value.findIndex((note) => note.id === noteId);
  if (index !== -1) {
    notes.value.splice(index, 1);
  }
};

</script>

<template>
    <main>
      <div v-if="showModel" class="overlay">
        <div class="modal">
          <textarea v-model.trim ="newNote" name="note" id="note" cols="30" rows="10"></textarea>
          <h3 v-if="errorMsg"> Length of the note should be greater than 9</h3>
          <button @click="addNote">Add Note</button>
          <button class="close" @click="showModel = false">Close</button>
        </div>
        <!--   details in my notion

          <div v-show="showModel" class="overlay">
        <div class="modal">
          <textarea name="note" id="note" cols="30" rows="10"></textarea>
          <button>Add Note</button>
          <button class="close" @click="showModel = false">Close</button>
        </div> 
      -->
      </div>  
      <div class="container">
        <header>
          <h1>Notes</h1>
          <button @click="showModel = true">+</button>
        </header>
        <div class="cards-container">

          <div 
          v-for="note in notes" 
          :key="note.id"
          class="card"
           :style="{backgroundColor: note.backgroundcolor}"
           >
           
            <p class="main-text">{{ note.text }}</p>
            <p class="date">{{ note.date.toLocaleDateString("en-US")}}</p>
            <button @click="deleteNote(note.id)">Delete</button>
          </div>
        </div>
      </div>
    </main>
  </template>
  
  <style scoped>
    main {
      height: 100vh;
      width: 100vw
    }

    .container {
      max-width: 1000px;
      padding: 10px;
      margin: 0 auto;
    }
  
    header {
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
  
    h1 {
      font-weight: bold;
      margin-bottom: 25px;
      font-size: 75px;
      color: rgb(0, 0, 0);
    }
  
    header button {
      border: none;
      padding: 10px;
      width: 50px;
      height: 50px;
      cursor: pointer;
      background-color: rgb(21,20,20);
      border-radius: 100%;
      color: white;
      font-size: 20px;
    }
  
    .card {
      width: 225px;
      height: 225px;
      background-color: rgb(237, 182, 44);
      padding: 10px;
      border-radius: 15px;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      margin-right: 20px;
      margin-bottom: 20px;
    }
  
    .date {
      font-size: 12.5px;
      font-weight: bold;
    }
  
    .cards-container {
      display: flex;
      flex-wrap: wrap;
    }
  
    .overlay {
      position: absolute;
      width: 100%;
      height: 100%;
      background-color: rgba(0,0,0,0.77);
      z-index: 10;
      display: flex;
      align-items: center;
      justify-content: center;
    }
  
    .modal {
      width: 750px;
      background-color: white;
      border-radius: 10px;
      padding: 30px;
      position: relative;
      display: flex;
      flex-direction: column;
    }
  
    .modal button {
      padding: 10px 20px;
      font-size: 20px;
      width: 100%;
      background-color: blueviolet;
      border: none;
      color: white;
      cursor: pointer;
      margin-top: 15px
    }
  
    .modal .close {
      background-color: rgb(193, 15, 15);
      margin-top: 7px;
    }
    .modal h3{
      color: red;
    }

  </style>