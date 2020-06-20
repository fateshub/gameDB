<template>
  <div>
    <p> Search Results : {{input}} </p>

  <div id="inputbox">
    <el-input placeholder="Please input your name" v-on:keyup.enter="gamesearch()" v-model="input"></el-input>
      <el-button type="primary" round  @click="gamesearch(input)">Search</el-button>
  </div>
  <p> released: {{ game.released }}</p>
    <p> achievements: {{ game.achievements_count }}</p>

  </div>
</template>

<script>
const axios = require('axios');

export default {
  name: 'SearchGame',
  data() {
      return {  
          input: "",
          game: ""
      }
  },
  methods:{
  async gamesearch(name){
      let config ={
        headers: {
          "x-rapidapi-key": "1bdb332de3mshd9b80befa33f780p1a27fejsn05c82ca36ec3"
        }
      }
      const api = await axios.get('https://rawg-video-games-database.p.rapidapi.com/games/'+name.toUpperCase().replace(/ /g,"-"), config)
      this.game = api.data;
    }
  }
}
</script>

<style>
#inputbox{
max-width: 20%;
min-width: 10rem;
margin: 0 auto;

}

</style>