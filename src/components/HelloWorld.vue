<template>
  <div class="main">
    <p>{{ text }} : {{input}}</p>
  <div id="inputbox">
    <el-input placeholder="Please input your name" v-model="input"></el-input>
  </div>
  <div  v-bind:key="game.id"  v-for="game in list" >
    <div>
  <el-button type="text" @click="gamestats(game.id)"> {{ game.name }} </el-button>
  <p v-if="game.id == score.id">Score: {{score.rating}}</p>
    </div>
  </div>
          <el-button @click="gamedb">Click Me</el-button>

  </div>
</template>
  
<script>
const axios = require('axios');
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
data(){
    return{    text: "hello",
    input: "",

    list: "",
    score: ""
  }}, 
  methods:{
    async gamedb(){
      let config ={
        headers: {
          "x-rapidapi-key": "1bdb332de3mshd9b80befa33f780p1a27fejsn05c82ca36ec3"
        }
      }
      const api = await axios.get('https://rawg-video-games-database.p.rapidapi.com/games', config)
      this.list = api.data.results;
    }, 
     async gamestats(gid){
      let config ={
        headers: {
          "x-rapidapi-key": "1bdb332de3mshd9b80befa33f780p1a27fejsn05c82ca36ec3"
        }
      }
      const api = await axios.get('https://rawg-video-games-database.p.rapidapi.com/games/'+gid, config)
      this.score = api.data;
    }
  }

}
    


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
#inputbox{
max-width: 20%;
min-width: 10rem;
margin: 0 auto;
}
</style>
