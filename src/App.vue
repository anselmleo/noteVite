<template>
  <main>
    <div class="modal">
      <textarea name="note" id="note" cols="30" rows="10"></textarea>
      <button></button>
    </div>
    <div class="container">
      <header>
        <h1>Notes</h1>
        <button>+</button>
      </header>
      <div class="cards-container">
        <div class="card">
          <p class="main-text">Lorem ipsum, dolor sit amet consectetur adipisicing elit. Dicta numquam expedita laudantium commodi saepe incidunt deleniti reiciendis eum aliquid qui.</p>
          <p class="date">12-12-2023</p>
        </div>
        <div class="card">
          <p class="main-text">Lorem ipsum, dolor sit amet consectetur adipisicing elit. Dicta numquam expedita laudantium commodi saepe incidunt deleniti reiciendis eum aliquid qui.</p>
          <p class="date">12-12-2023</p>
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
    background-color: orange;
    margin-right: 10px;
    padding: 10px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  .date { 
    font-weight: bold;
  }
</style>