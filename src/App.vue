<template>
  <h1>Everyone loves reaction games, right? RIGHT????</h1>
  <h2>..please just click a damn block when you see it.</h2>
  <button @click="gameOn">Start</button>
  <blockForClicking v-if="gameStatus" @click="gameOff" />
  <p>{{ countingSeconds }} ms</p>
</template>

<script>
import blockForClicking from './components/blockForClicking.vue'

export default {
  name: 'App',
  data(){
    return{
      gameStatus:false,
      staticDelay: null,
      countingEvent: null,
      countingSeconds: 0
    }
  },
  components: {
    blockForClicking
  },
  methods:{
    gameOn(){
      this.staticDelay = 1000 + Math.random() * 2000; console.log (this.staticDelay);
      this.countingSeconds = 0;
      setTimeout(() => {
        this.gameStatus = true
        this.countingEvent = setInterval(() => {this.countingSeconds += 5}, 5)
      }, this.staticDelay) 
    },
    gameOff(){
      this.gameStatus = false;
      clearInterval(this.countingEvent);
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
</style>
