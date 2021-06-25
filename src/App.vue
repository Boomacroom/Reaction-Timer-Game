<template>

<div class="backdrop" @click.self="cheaterDetected">
  <h1>Boom's Reaction Timer</h1>
  <button class="button" @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay='delay' @end="endGame" />
  <Results :result='score' v-if="showResults"/>
</div>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  components: {
    Block, Results
  },
  methods: {
    start() {
      this.delay = 1000 + Math.random() * 5000
      this.isPlaying = true
      console.log(this.delay)
      this.showResults = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
    },
    cheaterDetected() {
      this.isPlaying = false
      alert("Cheater Detected! Remember when you cheat, you're only cheating yourself...")
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
  color: #444;
  margin-top: 60px;
}
body{
  margin: 0;
}

.button {
  position: relative;
  background-color: #4CAF50;
  border: none;
  font-size: 28px;
  color: #FFFFFF;
  padding: 20px;
  width: 200px;
  text-align: center;
  transition-duration: 0.4s;
  text-decoration: none;
  overflow: hidden;
  cursor: pointer;
}

.button:after {
  content: "";
  background: #f1f1f1;
  display: block;
  position: absolute;
  padding-top: 300%;
  padding-left: 350%;
  margin-left: -20px !important;
  margin-top: -120%;
  opacity: 0;
  transition: all 0.8s
}

.button:active:after {
  padding: 0;
  margin: 0;
  opacity: 1;
  transition: 0s
}
.backdrop {
    top: 0;
    position: fixed;
    width: 100%;
    height: 100%;
  }
</style>
