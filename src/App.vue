<script setup>
  import {ref, computed} from 'vue'
  let showModal = ref(false)
  let note = ref('')
  let notes = ref([])
  let formattedDateNow =  computed(() => {
    const options = {day: '2-digit', month: '2-digit', year: 'numeric', hour: 'numeric', minute: 'numeric', second: 'numeric', timeZone: 'UTC'}
    return new Date().toLocaleDateString('en-GB', options)
  })
  const addNote = () => {
    if(note.value==='' || note.value.length<10) return alert('Note must be mininum of 10 characters')
    notes.value.push({
      id: notes.value.length+1,
      note: note.value,
      backgroundColor: getRandomColor(),
      date: new Date()
    })
    note.value=''
    showModal.value=false
  }

  const getRandomColor = () => `hsl(${Math.random() * 360}, 100%, 75%)`

</script>

<template>
  <main>
    <div class="modal" v-if="showModal">
      <div class="textarea">
        <textarea name="note" id="note" cols="30" rows="10" v-model="note"></textarea>
        <button class="close" @click="showModal=false">x</button>
      </div>
      <button class="addNote" @click="addNote">Add Note</button>
    </div>
    <div class="container">
      <header>
        <h1>Notes</h1>
        <button @click="showModal=true">+</button>
      </header>
      <div class="cards-container">
        <div class="card" v-for="note in notes" :key="note.id" :style="{backgroundColor: note.backgroundColor}">
          <p class="main-text">{{note.note}}</p>
          <p class="date">{{note.date}}</p>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
  main {
    width: 100vw;
    height: 100vh;
    background-color: white
  }

  .container {
    max-width: 1000px;
    padding: 10px;
    margin: 0 auto
  }

  header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 30px 0 30px 0;
  }

  header button {
    font-size: xx-large;
    width: 40px;
    height: 40px;
    border-color: black;
    border-radius: 100%;
    color: white;
    background-color: black;
  }

  .cards-container {
    display: flex;
    flex-wrap: wrap;
  }

  .card {
    width: 200px;
    height: 250px;
    border-radius: 5%;
    /* background-color: hsl(201.00097036639724, 100%, 75%); */
    margin-right: 10px;
    margin-bottom: 10px;
    padding: 10px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  .modal {
    display: flex;
    flex-direction: column;
    justify-content: center;
    position: absolute;
    width: 100%;
    height: 100%;
    background-color: rgba(25,25,25,.8);
    align-items: center;
  }

  .modal .textarea {
    display: flex;
    justify-content: center;
    background-color: yellow;
    /* width: 5000px; */
  }

  .modal .close {
    color: white;
    position: absolute;
    z-index: 5;
    height: 20px;
    width: 20px;
    background-color: rgb(201, 80, 4);
    border: none;
    border-radius: 5%;
    right: 645px;
  }

  .modal textarea {
    width: 500px;
    height: 200px;
    border: none;
  }

  .modal .addNote {
    width: 500px;
    height: 30px;
    border-radius: 5px;
    background-color: rgb(201, 80, 4);
    color: white;
    border: none;
  }
  
</style>