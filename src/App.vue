<template>
  <h1>Everyone loves reaction games, right? RIGHT????</h1>
  <h2>..please just click a damn block when you see it.</h2>
  <button @click="gameOn">Start</button>
  <blockForClicking v-if="gameStatus" />
</template>

<script>
import blockForClicking from './components/blockForClicking.vue'

export default {
  name: 'App',
  data(){
    return{
      gameStatus:false,
      staticDelay: 2000,
      dynamicDelay: null
    }
  },
  components: {
    blockForClicking
  },
  methods:{
    gameOn(){
      this.staticDelay += Math.random() * 1000; console.log (this.staticDelay);
      this.dynamicDelay = setTimeout(() => {this.gameStatus = true}, this.staticDelay) 
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
