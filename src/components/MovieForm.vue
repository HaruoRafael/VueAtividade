<template>
    <form @submit.prevent="addMovie">
      <h2>Cadastro de Filmes</h2>
  
      <div class="input-group">
        <label for="title">Título:</label>
        <input type="text" id="title" v-model="newMovie.title" required />
      </div>
  
      <div class="input-group">
        <label for="year">Ano:</label>
        <input type="number" id="year" v-model="newMovie.year" min="1888" max="2099" required />
      </div>
  
      <div class="input-group">
        <label for="genre">Gênero:</label>
        <input type="text" id="genre" v-model="newMovie.genre" required />
      </div>
  
      <button type="submit">Cadastrar Filme</button>
    </form>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newMovie: {
          title: '',
          year: '',
          genre: ''
        }
      };
    },
    methods: {
      addMovie() {
        if (this.newMovie.title && this.newMovie.year && this.newMovie.genre) {
          this.$emit('movie-added', { ...this.newMovie });
          this.newMovie = { title: '', year: '', genre: '' }; // Limpa os campos
        } else {
          alert('Por favor, preencha todos os campos.');
        }
      }
    }
  };
  </script>
  
  <style scoped>
  form {
    max-width: 600px; /* Aumenta a largura do formulário */
    margin: 0 auto;
    padding: 30px;
    background-color: #f9f9f9;
    border-radius: 10px;
    box-shadow: 0px 6px 12px rgba(0, 0, 0, 0.15);
  }
  
  h2 {
    text-align: center;
    font-size: 24px;
    margin-bottom: 20px;
    color: #333;
  }
  
  .input-group {
    margin-bottom: 25px;
  }
  
  label {
    display: block;
    font-weight: bold;
    margin-bottom: 8px;
    font-size: 16px;
    color: #555;
  }
  
  input {
    width: 100%;
    padding: 12px;
    font-size: 16px;
    border: 1px solid #ddd;
    border-radius: 6px;
    box-sizing: border-box;
    transition: border-color 0.3s ease-in-out;
  }
  
  input:focus {
    border-color: #4caf50;
    outline: none;
  }
  
  button {
    width: 100%;
    background-color: #4caf50;
    color: white;
    padding: 14px;
    font-size: 18px;
    font-weight: bold;
    border: none;
    border-radius: 6px;
    cursor: pointer;
    transition: background-color 0.3s ease-in-out, transform 0.2s;
  }
  
  button:hover {
    background-color: #45a049;
    transform: translateY(-2px);
  }
  
  button:active {
    background-color: #3e8e41;
    transform: translateY(0);
  }
  </style>
  