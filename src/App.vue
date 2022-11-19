<script setup>
/*
I tried to create a handy webapp to keep track of all the movies I've watched this year and which was my favorite, but form bindings are confusing and it's not working properly :(

Can you help me fix it?

level 1: Update the movie list with a v-for loop so all movies in the provided file movies.json are rendered. Feel free to update/change the list to your likes, or to add more info for each movie.

level 2: Create a small "movie card" for each movie object in the list and display in it the title, a small poster picture, and the score of the movie.

level 3: Remove the duplicated & hardcoded code in the form binding for "My fav movie" selector 1, and use a v-for loop and attribute bindings to correctly build the options. (Note: you can change the binding variable 'favoriteMovie' below if needed)

level 4: I want it to be easy to see which one is my current favorite, so please add a "😍" emoji next to the title to my favorite movie in the list.

level 5: The score of each film is represented by a string with a value between "0" and "100". We can do better! Let's show between 1 to 5 stars in each film card, according to the score (tip: use a v-for loop here).

level 6: Fix the multiselectors 2, 3 of the movies I've watched this year. Remove the duplicated & hardcoded code in the form binding for both multi selectors, and use v-for loops and attribute bindings to correctly build the options. Keep in mind they should be synchronized! (keep using the same binding to the variable "watchedList" for both fields).

level 7: The multiselectors are nice, but it would be great to also have a checkbox on each film card to mark it as watched/not watched. Of course, it should be synchronized with the "watchedList" array!

bonus level: Apply your CSS magic and designer's touch to make the app look great!
*/

import { ref } from 'vue';
import movies from './assets/movies.json';
const favoriteMovie = ref('');
const watchedList = ref([]);
const rate =ref([]);

// function starRating(score) {
//   <span v-if="score >= 90">rate.value.push(Object.assign({}, ⭐ ⭐ ⭐ ⭐ ⭐))</span>
//   <span v-else-if="score >= 80">rate.value.push(Object.assign({}, ⭐ ⭐ ⭐ ⭐))</span>
//    <span v-else-if="score >= 60">rate.value.push(Object.assign({},⭐ ⭐ ⭐))</span>
//     <span v-else-if="score >= 40">rate.value.push(Object.assign({}, ⭐ ⭐ ))</span>
//     <span v-else>rate.value.push(Object.assign({},⭐))</span>
  
// }
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
      <input type="checkbox" id="checkbox" v-model="checked" /><br/>
<!-- <label for="checkbox" watchedList.value.push(movie.title)>Watched</label> -->
<span v-if="score >= 90">⭐ ⭐ ⭐ ⭐ ⭐</span>
  <span v-else-if="score >= 80">⭐ ⭐ ⭐ ⭐</span>
   <span v-else-if="score >= 60">⭐ ⭐ ⭐</span>
    <span v-else-if="score.value >= 40">⭐ ⭐</span>
    <span v-else>⭐</span>
<!-- <h3> {{rate}}</h3> -->
  </div>
  
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
  <div>
    <span>3 - Movies watched this year: {{ watchedList }}</span>
    <br />
    <br />

    <input type="checkbox" id="option1" value="Dune" v-model="watchedList" />
    <label for="option1">Dune</label>
    <br />

    <input type="checkbox" id="option2" value="?" v-model="watchedList" />
    <label for="option2">Everything, Everywhere, all at once</label>
    <br />
    <input type="checkbox" id="option3" value="?" v-model="watchedList" />
    <label for="option3">Top Gun: Maverick</label>
  </div>
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
</style>
