<template>
  <h1>Everyone loves reaction games, right? RIGHT????</h1>
  <h2>..please just click a damn block when you see it.</h2>
  <button class="btn" @click="gameOn">S T A R T</button>
  <blockForClicking v-if="gameStatus" @click="gameOff" />
  <div v-if="showResult">
     <p style="font-weight:bold">{{ countingSeconds }} ms</p>
     <p style="font-weight: bolder; font-size: larger; color:deeppink;">{{ result }}</p>
    </div>
 
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
      countingSeconds: 0,
      showResult: false,
      result: null
    }
  },
  components: {
    blockForClicking
  },
  methods:{
    gameOn(){
      this.staticDelay = 1000 + Math.random() * 2000; 
      this.showResult = false;
      this.countingSeconds = 0;
      setTimeout(() => {
        this.gameStatus = true
        this.countingEvent = setInterval(() => {this.countingSeconds += 5}, 5)
      }, this.staticDelay) 
    },
    gameOff(){
      this.gameStatus = false;
          clearInterval(this.countingEvent);
          if (this.countingSeconds < 210) this.result = 'An FPS player';
      else if (this.countingSeconds < 320) this.result = "You're pretty good";
      else this.result = 'Hello, grandma';
      this.showResult = true;
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
.btn {
  margin: 10px auto;
  padding: 20px 40px;
  background-color:greenyellow;
}
.btn:active {
            transform: scale(0.8);
            box-shadow: 3px 2px 22px 1px rgba(0, 0, 0, 0.24);
        }
</style>
