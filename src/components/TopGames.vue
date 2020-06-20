<template>
  <div class="main">
  <el-row>
  <div v-bind:key="game.id"  v-for="game in list" >
    <el-col :span="6"><div>
      <el-popover  placement="bottom"
    title="Score"
    width="200"
    trigger="click"
    >
    <div>
     <p v-if="game.id == score.id & score.rating > 4" class="high-score"  > {{score.rating}}</p>
         <p v-else-if="game.id == score.id & score.rating <= 4" class="low-score"  > {{score.rating}}</p>
 </div>
  <el-button slot="reference" id="gamename" type="text" @click="gamestats(game.id)"> {{ game.name }} </el-button>
 
  </el-popover>
    </div></el-col>
  </div>
 </el-row>
  </div>
</template>
  
<script>
const axios = require('axios');
export default {
  name: 'TopGames',
  
data(){
    return{    

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
  },
   beforeMount(){
     this.gamedb()
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

#gamename{
  margin-right: 0%;
}


.high-score{
  color: #42b983;
}
.low-score{
  color: red;
}
</style>
