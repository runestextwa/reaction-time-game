<template>
  <h1>Everyone loves reaction games, right? RIGHT????</h1>
  <H2>..please just click a damn block when you see it.</H2>
  <blockForClicking />
</template>

<script>
import blockForClicking from './components/blockForClicking.vue'

export default {
  name: 'App',
  components: {
    blockForClicking
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
