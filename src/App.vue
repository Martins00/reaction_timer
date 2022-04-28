<template>
  <h1>Reaction Timer with Vue</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <p v-if="showResult">Reaction time: {{score}}ms</p>
</template>

<script>
 import Block from './components/Block.vue'

export default {
  name: 'App',
  components: { Block },
  data(){
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false
    }    
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 4000
      this.isPlaying = true
      this.showResult = false
    },
    endGame(reactionTime) {
     this.showResult = true
     this.score = reactionTime
     this.isPlaying = false
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
