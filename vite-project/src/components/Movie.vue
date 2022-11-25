<script setup>
import { ref } from "vue";
import axios from "axios";
 
const id = ref("");
const movie = ref(null);
 
const getMovies = async () => {
  const data = id.value;
  movie.value = (
    await axios.get(`https://api.themoviedb.org/3/movie/${data}`, {
      params: {
        api_key: "0a4dbc5e3b74420548bdd09d59591acf",
        append_to_response: "videos",
      },
    })
  ).data;
};
</script>
 
<template>
  <select v-model="id">
    <option value="293660">Deadpool</option>
    <option value="496243">Parasite</option>
    <option value="810693">Jujutsu Kaisen</option>    
    <option value="91314">Transformers</option>
    <option value="378064">A Silent Voice</option>
    <option value="453127">Midnight Runners</option>
    <option value="550">Fight Club</option>  
    <option value="78">Blade Runner</option>  
    <option value="1359">American Psycho</option>  
    <option value="68726">Pacific Rim</option>  
  </select>
  <button @click="getMovies">Get</button>
  <div v-if="movie" class="movie-container">
    <h1>{{movie.original_title}}</h1>
    <p>Overview: {{movie.overview}}</p>
    <img :src="`https://image.tmdb.org/t/p/w500/${movie.poster_path}`">
    <iframe :src="`https://www.youtube.com/embed/${movie.videos.results.filter((video) => video.type === 'Trailer').at(0).key}`"></iframe>
    <p>Release Date: {{movie.release_date}} | Movie Popularity: {{movie.popularity}}</p>
    <p>Adult: {{movie.adult}} | Language: {{movie.original_language}}</p>
    <p>Vote Average: {{movie.vote_average}} | Vote Count: {{movie.vote_count}}</p>
 
  </div>
</template>
 
<style scoped>
*{
  margin: 0;
  padding: 5px;
  font-family:'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif
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
  margin-left:30%;
  aspect-ratio: 2 / 3;
  border: 10px solid black;
  height: 700px;
  background-color: rgb(159, 92, 221);
}
 
iframe{
  border-radius:50px;
  margin-bottom: 1%;
  margin-left: 20%;
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
 
 

