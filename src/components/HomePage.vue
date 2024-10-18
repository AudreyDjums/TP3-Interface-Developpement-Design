<template>
    <div class="home-page">
      <h1>Welcome to the Home Page</h1>
      <p>Il s'agit de la page d'accueil de notre projet Vue.js</p>
      <header>
        <AsyncButton color="primary" @click="handlePrimaryClick">Primary Button</AsyncButton>
        <AsyncButton color="warn" @click="handleWarnClick">Warn Button</AsyncButton>
        <AsyncButton color="danger" @click="handleDangerClick">Danger Button</AsyncButton>
      </header>
    </div>
  </template>
  
  <script>
  import AsyncButton from './AsyncButton.vue';
  
  export default {
    name: 'HomePage',
    components: {
      AsyncButton
    },
    data() {
      return {
        clickCount: 0 // Initialize the click counter
      };
    },
    methods: {
      async handlePrimaryClick() {
        this.clickCount++; // Increment the click counter
        alert(`Primary button clicked! Waiting for ${this.clickCount} seconds.`);
        await new Promise(resolve => setTimeout(resolve, this.clickCount * 10000)); // Wait time increases with each click
      },
      async handleWarnClick() {
        this.clickCount++;
        alert(`Warn button clicked! Waiting for ${this.clickCount} seconds.`);
        await new Promise(resolve => setTimeout(resolve, this.clickCount * 10000));
      },
      async handleDangerClick() {
        this.clickCount++;
        alert(`Danger button clicked! Waiting for ${this.clickCount} seconds.`);
        await new Promise(resolve => setTimeout(resolve, this.clickCount * 10000));
      }
    }
  };
  </script>
  
  <style scoped>
  .home-page {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    background-color: #f0f0f5;
    text-align: center;
    padding: 0 20px;
  }
  
  h1 {
    font-size: 2.5rem;
    color: #4caf50;
    margin-bottom: 20px;
  }
  
  p {
    font-size: 1.2rem;
    color: #555;
    margin-bottom: 20px;
  }
  
  header {
    display: flex;
    gap: 10px; /* Space between buttons */
    margin-top: 20px; /* Space above buttons */
  }
  </style>
  