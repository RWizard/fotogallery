<template>
<div class="container">
  <div class="films" >
    <ul>
      <p v-for="film in films" :key="film.data.ts">
        {{film.data.title.Title}} <br>
        <img :src="film.data.title.Poster">
      </p> 
    </ul> 
  </div>
</div> 
</template>

<script>

export default {

    name: "app",
    data() {
      return {
        films: []
      };
    },
    
    async mounted() {
      const res = await fetch(
        "http://localhost:3000/api/get_films"
      );
      const films = await res.json();
      this.films = films.data; 
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
