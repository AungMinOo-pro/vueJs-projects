<template>
  <h1>How fast can u catch me?</h1>
  <button class="btn" @click="start" :disabled="isPlaying">play</button>
  <div v-if="end">
    <Result :score="score"/>
  </div>
  <div v-if="isPlaying">
    <Block :delay="delay" @endGame="endGame"/>
  </div>
</template>

<script>
  import Block from "./components/Block.vue"
  import Result from "./components/Result.vue"

export default {
  name: 'App',
  components: {
    Block,
    Result,
  },
  data(){
    return{
      isPlaying : false,
      delay:null,
      score:0,
      end:false
    }
  },
  methods:{
    start(){
      this.isPlaying=true;
      this.delay = 2000+Math.random()*5000;
    },
    endGame(score){
      this.score= score;
      this.isPlaying=false;
      this.end=true;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.btn{
  padding: 10px 30px; 
  background-color: greenyellow;
  border: none;
  border-radius: 10px;
  font-weight: bold;
  color: purple;
  font-size: 20px;
  box-shadow: 10px 5px rgba(0, 0, 0, 0.2);
}
button:disabled{
  background: #086972;
  color: black;
}
</style>
