<script setup>
/*
I tried to create a handy webapp to keep track of all the movies I've watched this year and which was my favorite, but form bindings are confusing and it's not working properly :(

Can you help me fix it?

level 1: Update the movie list with a v-for loop so all movies in the provided file movies.json are rendered. Feel free to update/change the list to your likes, or to add more info for each movie.

level 2: Create a small "movie card" for each movie object in the list and display in it the title, a small poster picture, and the score of the movie.

level 3: Remove the duplicated & hardcoded code in the form binding for "My fav movie" selector 1, and use a v-for loop and attribute bindings to correctly build the options. (Note: you can change the binding variable 'favoriteMovie' below if needed)

level 4: I want it to be easy to see which one is my current favorite, so please add a "😍" emoji next to the title to my favorite movie in the list.

level 5: The score of each film is represented by a string with a value between "0" and "100". We can do better! Let's show between 1 to 5 stars in each film card, according to the score (tip: use a v-for loop here).

 
*/

import { ref } from 'vue';
import movies from './assets/movies.json';
const favoriteMovie = ref('');
const watchedList = ref([]);
const rate =ref([]);

</script>



<template>
  <h3>Movie list</h3>
  <div>
    <ul  v-for="movie in movies">

    <div class="card">
      
      <img class='cardimg' :src=movie.picture alt="Avatar" style="width:100%">
      <div class="container">
      <h4><b>Movie Title : {{movie.title}}</b>
      <span class="emoji" v-if="favoriteMovie === movie.title">😍</span></h4> 
      <p>Movie Score :  {{movie.score}}</p> 
      <input type="checkbox" id="checkbox" v-model="checked" /> Watched<br/>
<!-- <label for="checkbox" watchedList.value.push(movie.title)>Watched</label> -->
<span v-if="movie.score >= 90">⭐ ⭐ ⭐ ⭐ ⭐</span>
  <span v-else-if="movie.score >= 80">⭐ ⭐ ⭐ ⭐</span>
   <span v-else-if="movie.score >= 60">⭐ ⭐ ⭐</span>
    <span v-else-if="movie.score >= 40">⭐ ⭐</span>
    <span v-else>⭐</span>
  </div><br/>
  
</div>

      
    </ul>
  </div>

  <hr />
  <h3>Controls</h3>
  <div>
    <span>1 - My fav movie: {{ favoriteMovie || "no favorite movie selected"  }}</span>
    <br />
    <br />
    <select v-model="favoriteMovie">
      <option disabled value="">Please select a favorite!</option>
      <option v-for="movie in movies" :value="movie.title"> 
        {{ movie.title }}
      </option>
    </select>
  </div>

  <hr />

  <div>
    <span>2 - Movies watched this year: {{ watchedList }}</span>
    <br />
    <br />
    <select v-model="watchedList" multiple>
      <option>Dune</option>
      <option>Everything, Everywhere, all at once</option>
      <option>Top Gun: Maverick</option>
    </select>
  </div>

  <hr />
  
</template>

<style scoped>
.card {
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s;
  width: 18rem;
}

.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
}

.container {
  padding: 1px 16px;
}

.cardimg{
   height:13rem;
}

.sideview{
  width :13rem;
  background-color: coral;
}
</style>
