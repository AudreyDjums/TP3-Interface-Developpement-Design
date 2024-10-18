<template>
    <header class="base-header">
      <nav>
        <div class="nav-container">
          <ul class="nav-links">
            <li><a href="#">Home</a></li>
          </ul>
          <div class="user-info">
            <span class="username">Hello, Djumo!</span>
          </div>
        </div>
      </nav>
    </header>
  </template>
  
  <script>
  export default {
    name: 'BaseHeader',
  };
  </script>
  
  <style scoped>
  .base-header {
    background-color: #4caf50;
    padding: 1rem;
    color: white;
  }
  
  .nav-container {
    display: flex; 
    justify-content: space-between; 
    align-items: center; 
  }
  
  .nav-links {
    list-style: none;
    padding: 0;
    margin: 0;
    display: flex; 
  }
  
  .nav-links li {
    margin: 0 15px;
  }
  
  .nav-links li a {
    color: white;
    text-decoration: none;
    font-weight: bold;
    transition: color 0.3s ease;
  }
  
  .nav-links li a:hover {
    color: #e0e0e0;
  }
  
  .user-info {
    font-size: 1.1rem; 
    color: white; 
    margin-left: 20px; 
  }
  </style>
  