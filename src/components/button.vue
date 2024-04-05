<template>
    <div class="corner-buttons">
      <button class="button" @click="goHome">Home</button>
      <button class="button" @click="logout">Logout</button>
    </div>
  </template>
  
  <script>
  export default {
    methods: {
      goHome() {
        // Logika untuk pergi ke halaman utama
        console.log("Navigating to home...");
      },
      logout() {
        // Logika untuk logout pengguna
        console.log("Logging out...");
      }
    }
  };
  </script>
  
  <style scoped>
  .corner-buttons {
    position: fixed;
    top: 10px;
    right: 10px;
    z-index: 1000;
    backdrop-filter: blur(10px); /* Efek blur untuk latar belakang */
  }
  
  .button {
    border: 1px solid lightblue; /* Border warna biru muda */
    background-color: transparent;
    padding: 10px 15px;
    margin-left: 10px;
    cursor: pointer;
    color: white;
  }
  
  .button:hover {
    background-color: lightblue;
    color: black;
  }
  </style>
  