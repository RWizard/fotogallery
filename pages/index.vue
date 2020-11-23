<template>
<div class="container">
  <div class="films" >
    <ul>
      <nuxt-link :to='/films/ + film.data.ref["@ref"].id' v-for="film in films" :key='film.data'>
        {{film.data.title.Title}} <br>
      </nuxt-link> 
    </ul> 
  </div>
</div> 
</template>

<script>

export default {

    name: "app",
    data() {
      return {
        films: [],
        id: ""
      };
    },
    
    async mounted() {
      const res = await fetch(
        "http://localhost:3000/api/actors/films"
      );
      const films = await res.json();
      this.films = films.data; 
    },
    async getFilm(userId) {
      console.log(userId)
    }
   }

</script>

<style>

.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

</style>
