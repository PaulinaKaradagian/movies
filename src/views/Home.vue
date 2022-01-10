<template>
  <div class="home">
    <div class="feature-card">
      <router-link to="/movie/tt0409591">
              <img src="https://i.pinimg.com/564x/e0/f4/ba/e0f4baaf2bf43934f69db75d4726f9fb.jpg" 
              alt="Movies Sign" class="featured-img" />
              <div class="detail">
                <h3>Movie Catalogue</h3>
                <p>
                  This is a movie catalogue made with Vue.js. It works with the API provided by IMDB.
                  The images are provided by the API and I found some might be missing. 
                  You can search by title of the movie or title of games too. BEST FOR MOBILES, not so good on desktop.

                </p>
              </div>

      </router-link>


    </div>
      <form @submit.prevent= "SearchMovies()" class="search-box">
        <input type="text" placeholder= "What are you looking for?" v-model="search"/>
        <input type= "submit" value= "Search" />
      </form>
      <div class="movies-list">
        <div class="movie" v-for="movie in movies" :key="movie.imdbID">
          <router-link :to= "'/movie/' + movie.imdbID" class= "movie-link">
            <div class="product-image">
              <img :src="movie.Poster" alt="Movie Poster" />
              <div class="type">
                {{movie.Type}}
              </div>
              <div class= "details">
                <p class="year">{{movie.Year}}</p>
                <h3 class="sub">{{movie.Title}}</h3>
              
              </div>
            </div>
          </router-link>
        </div>
      </div>
  </div>
</template>

<script>
// @ is an alias to /src
import {ref} from 'vue'
//import enviroment from '@/enviroment'
export default {
 setup(){
   const search = ref("")
   const movies = ref([])

   const SearchMovies = () =>{
     if(search.value != ""){
       fetch(`http://www.omdbapi.com/?i=tt3896198&apikey=391e77e7&s=${search.value}`)
       .then(response => response.json())
       .then(data => {
          movies.value = data.Search
          search.value = ""
        })
       
     }
   }

   return{
     search,
     movies,
     SearchMovies,
   }
 }  
}
</script>

<style scoped>



.feature-card {
	position: relative;
}
 .featured-img {
	display: block;
	width: 100%;
	height: 300px;
	object-fit: cover;
	position: relative;
	z-index: 0;
}
 .detail {
 position: absolute;
 left: 0;
 right: 0;
 bottom: 0;
 background-color: rgba(0, 0, 0, 0.6);
 padding: 16px;
 z-index: 1;
}
 h3 {
 color: #fff;
 margin-bottom: 16px;
}
 p {
 color: #fff;
}
 .search-box {
 display: flex;
 flex-direction: column;
 justify-content: center;
 align-items: center;
 padding: 16px;
}
 input {
 display: block;
 appearance: none;
 border: none;
 outline: none;
 background: none;
}
 input[type="text"] {
 width: 100%;
 color: #fff;
 background-color: #496583;
 font-size: 20px;
 padding: 10px 16px;
 border-radius: 8px;
 margin-bottom: 15px;
 transition: 0.4s;
}
 input[type="text"]::placeholder {
 color: #f3f3f3;
}
 input[type="text"]:focus {
 box-shadow: 0px 3px 6px rgba(0, 0, 0, 0.2);
}
 input[type="submit"] {
 width: 100%;
 max-width: 300px;
 background-color: #42b883;
 padding: 16px;
 border-radius: 8px;
 color: #fff;
 font-size: 20px;
 text-transform: uppercase;
 transition: 0.4s;
}
 input[type="submit"]:active {
 background-color: #3b8070;
}
 .movies-list {
 display: flex;
 flex-wrap: wrap;
 margin: 0px 8px;
}
 .movie {
 max-width: 50%;
 flex: 1 1 50%;
 padding: 16px 8px;
}
 .movie-link {
 display: flex;
 flex-direction: column;
 height: 100%;
}
 .product-image {
 position: relative;
 display: block;
}
 img {
 display: block;
 width: 100%;
 height: 275px;
 object-fit: cover;
}
 .type {
 position: relative;
 padding: 8px 16px;
 background-color: #42b883;
 color: #fff;
 bottom: 16px;
 left: 0px;
 text-transform: capitalize;
}
 .details {
 background-color: #496583;
 padding: 18px 12px;
 flex: 1 1 100%;
 border-radius: 0px 0px 8px 8px;
}
 .year {
 color: #aaa;
 font-size: 14px;
}
 .sub {
 color: #fff;
 font-weight: 600;
 font-size: 16px;
}
 
</style>
