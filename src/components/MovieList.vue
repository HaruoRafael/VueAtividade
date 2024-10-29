<template>
    <ul class="movie-list" v-if="movies.length > 0">
      <li v-for="(movie, index) in movies" :key="index">
        <div class="movie-info">
          <span class="movie-title">{{ movie.title }}</span>
          <span class="movie-year">{{ movie.year }}</span>
          <span class="movie-genre">{{ movie.genre }}</span>
        </div>
        <button @click="deleteMovie(index)">Excluir</button>
      </li>
    </ul>
  </template>
  
  <script>
  export default {
    props: {
      movies: {
        type: Array,
        required: true
      }
    },
    methods: {
      deleteMovie(index) {
        this.$emit('delete-movie', index);
      }
    }
  };
  </script>
  
  <style scoped>
  .movie-list {
    margin-top: 20px;
    padding: 0;
    list-style-type: none;
    max-width: 600px;
    margin: 0 auto;
  }
  
  .movie-list li {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 15px;
    margin-bottom: 15px;
    border-radius: 8px;
    background-color: #f3f3f3;
    box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
    transition: transform 0.2s ease-in-out;
  }
  
  .movie-list li:hover {
    transform: translateY(-3px);
  }
  
  .movie-info {
    display: flex;
    flex-direction: column;
  }
  
  .movie-title {
    font-weight: bold;
    font-size: 18px;
    color: #333;
  }
  
  .movie-year, .movie-genre {
    font-size: 14px;
    color: #777;
  }
  
  button {
    background-color: #f44336;
    color: white;
    padding: 8px 12px;
    font-size: 14px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.3s ease-in-out;
  }
  
  button:hover {
    background-color: #e53935;
  }
  </style>
  