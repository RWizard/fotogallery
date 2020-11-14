<template>
  <div class="container">
    <div class="actors">
    </div>
    <button @click="$fetch">Загрузить актеров</button> 
    <br>
  <ul id="example-1">
    <li v-for="film in films" :key="film">
      {{ films.data.data.title.Director }}
    </li>
  </ul>  
</div>

</template>

<script>
export default {
    data() {
      return {
        films: []
      }
    },
    async fetch() {
      this.films = await fetch(
        'http://localhost:3001/api/filmlist'
      ).then(res => res.json())
      films = films.data
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



.links {
  padding-top: 15px;
}
</style>
