<template>
 
 <h1>Let's play a game </h1>
 <button @click="start" :disabled="isPlaying">Play</button>
<Block  v-if="isPlaying" :delay="delay"  @end="endGame">
</Block>
<p v-if="showResults"> Reaction time : {{ score }} ms</p>
<Results v-if="showResults" :score="score"/>
</template>

<script>
 
 import Block from './components/Block.vue'
 import Results from './components/Results.vue'

export default {
  name: 'App',
  components: { Block , Results },
  data() {
    return {
      isPlaying: false,
      delay: null ,
      score: null, 
      showResults: false ,
    }
  },
  methods: {
    start(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactionTime){
     this.score= reactionTime 
     this.isPlaying = false
     this.showResults= true
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
  color: #041627;
  margin-top: 60px;
}
button{
  background: rgb(120, 115, 124);
  color: #ffffff;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
}
button:hover{
  background-color: rgb(103, 23, 168);
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
