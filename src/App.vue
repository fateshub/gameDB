<template>
  <div id="app">
  <el-tabs v-model="activeName"  @tab-click="this.$refs.gamedb()">
    <el-tab-pane label="Top Games" name="first">  
       <TopGames />
    </el-tab-pane>
     <el-tab-pane label="Search" name="second">  
       <SearchGame />
    </el-tab-pane>
         <el-tab-pane>  
<span slot="label">
 <el-avatar :size="40" src="./assets/logo.png" :fit="cover"> </el-avatar>
</span>
                  </el-tab-pane>

  </el-tabs>         

  </div>
</template>

<script>
import TopGames from './components/TopGames.vue'
import SearchGame from './components/SearchGame.vue'

export default {
  name: 'App',
  components: {
    TopGames,
    SearchGame
  },
  data: () => ({
      show: true
    }),
    methods: {
      handleClick(tab, event) {
        console.log(tab, event);
        this.$emit('myevent')
      }
    }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat&display=swap');

#app {
font-family: 'Montserrat', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: black;
  
  margin: auto;

}


</style>
