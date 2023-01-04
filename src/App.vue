<template>
 <h1>REACTION TIMER GAME</h1>
 <button @click="start" :disabled="onGame">Play</button>
  <!-- <h1 v-if="showScore">Reaction Time: {{score}} ms</h1> -->
  <Result v-if="showScore" :score="score"/>

 <Block v-if="onGame" :delay="delay" @end="endGame"/>
</template>

<script>
import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  components: {
    Block,
    Result
  },
  data(){
    return{
     onGame: false,
     delay: null,
     score: null,
     showScore: false,
    }
  },
  methods:{
    start(){
      this.onGame = true
      this.showScore = false
      this.delay = 2000 + Math.random() * 5000
    },
    endGame(reactTime){
      this.score = reactTime
      this.onGame = false
      this.showScore = true

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
.active{
  color: pink;
}

</style>
