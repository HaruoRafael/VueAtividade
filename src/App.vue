<template>
  <div id="app">
    <MovieForm @movie-added="addMovie" />
    <EmptyMessage :movies="movies" />
    <MovieList :movies="movies" @delete-movie="deleteMovie" />
  </div>
</template>

<script>
import MovieForm from './components/MovieForm.vue';
import MovieList from './components/MovieList.vue';
import EmptyMessage from './components/EmptyMessage.vue';

export default {
  components: {
    MovieForm,
    MovieList,
    EmptyMessage
  },
  data() {
    return {
      movies: []
    };
  },
  methods: {
    addMovie(movie) {
      this.movies.push(movie);
    },
    deleteMovie(index) {
      this.movies.splice(index, 1);
    }
  }
};
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  max-width: 400px;
  margin: 0 auto;
  text-align: center;
  color: #333;
  display:flex;
  flex-direction: column;
  row-gap: 1rem;
}
</style>