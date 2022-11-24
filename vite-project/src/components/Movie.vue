<script setup>
import { ref } from "vue";
import axios from "axios";

const id = ref("");
const movie = ref(null);

const getMovies = async () => {
  const data = id.value;
  movie.value = (
    await axios.get("https://api.themoviedb.org/3/search/movie", {
      params: {
        api_key: "0a4dbc5e3b74420548bdd09d59591acf",
        query: data,
      },
    })
  ).data;
};
</script>

<template>
  <select v-model="id">
    <option value="Deadpool">Deadpool</option> <!-- 293660 -->
    <option value="Mugen Train">Demon Slayer</option>
    <option value="Jujutsu Kaisen">Jujutsu Kaisen</option>    
    <option value="Transformers">Transformers</option>
    <option value="A Silent Voice">A Silent Voice</option>
    <option value="Midnight Runners">Midnight Runners</option> 
    <option value="Fight Club">Fight Club</option>   
    <option value="Blade Runner">Blade Runner</option>  
    <option value="American Psycho">American Psycho</option>   
    <option value="Pacific Rim">Pacific Rim</option>  
  </select>
  <button @click="getMovies">Get</button>
  <div v-if="movie" class="movie-container">
    <h1>{{movie.results[0].original_title}}</h1>
    <p>Overview: {{movie.results[0].overview}}</p>
    <!-- <img src = https://image.tmdb.org/t/p/w500 {{movie.results[0].poster_path}}> -->
    <p>Release Date: {{movie.results[0].release_date}} | Movie Popularity: {{movie.results[0].popularity}}</p>
    <p>Adult: {{movie.results[0].adult}} | Language: {{movie.results[0].original_language}}</p>
    <p>Vote Average: {{movie.results[0].vote_average}} | Vote Count: {{movie.results[0].vote_count}}</p>

  </div>
</template>

<style scoped>
*{
  margin: 0;
  padding: 5px;
  font-family:'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif
}
body {
  color: blueviolet;
}

select{
  color: white;
  border-radius:50px;
  text-align: center;
  margin-left:45%;
  border: 5px solid black;
  background-color: rgb(159, 92, 221);
}

button{
  color: white;
  border-radius:50px;
  text-align: center;
  border: 5px solid black;
  background-color: rgb(159, 92, 221);
}

p{
  color: white;
  text-align: center;
  border: 5px solid black;
  background-color: rgb(159, 92, 221);
  border-radius: 50px;
}

img{
  border-radius: 50px;
  margin-left:15%;
  aspect-ratio: 2 / 3;
  border: 10px solid black;
  height: 700px;
  background-color: rgb(159, 92, 221);
}

iframe{
  border-radius:50px;
  margin-bottom: 10%;
  margin-left: 15%;
  aspect-ratio: 16 / 9;
  height: 400px;
  border: 10px solid black;
  background-color: rgb(159, 92, 221);
}

h1{
  text-align: center;
  font-size: 100px;
  color: white;
  border: 5px solid black;
  background-color: rgb(159, 92, 221);
  border-radius: 50px;
}
</style>
