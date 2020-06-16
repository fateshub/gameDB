<template>
  <div class="main">
    <p>{{ text }} : {{input}}</p>
  <div id="inputbox">
    <el-input placeholder="Please input your name" v-model="input"></el-input>
  </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
data(){
    return{    text: "hello",
    input: ""
  }}
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
