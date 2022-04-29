<template>
  <h1>Reaction Timer with Vue</h1>
  <h3>Click on the box as soon as you see it!</h3>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
 <Result v-if="showResult" :score="score" />
</template>

<script>
import Result from './components/Result.vue'
 import Block from './components/Block.vue'
 

export default {
  name: 'App',
  components: { Block, Result },
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
      this.delay = 2000 + Math.random() * 5000
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

h1,h3{
  color: gray;
}

button{
  color: azure;
  background: green;
  padding: 1.3rem 1rem;
  border: none;
  border-radius: 10px;

}

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed
}
</style>
