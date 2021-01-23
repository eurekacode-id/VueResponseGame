<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <div class="welcome">
    <h1>
      {{ msg }}
    </h1>
    <div class="start" v-show="!isPlaying" @click.self="hitStart">
      {{ start }}
    </div>
  </div>
  <Block v-if="isPlaying" msg="Hit me!" :delay="delay" @hitblock="hitBlock"/>
  <Result :msg="resultMsg" :resultScore="resultScore" :showResult="showResult"/>
</template>

<script>
import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  data(){
    return{
      msg: "Test your reaction!",
      start: "S T A R T",
      isPlaying: false,
      delay: null,
      resultMsg: "",
      resultScore: "",
      showResult: false
    }
  },
  components: {
    Block,
    Result
  },
  methods: {
    hitStart: function(){
      this.isPlaying = true;
      this.showResult = false;
      this.delay = 1000 + Math.random() * 1000;
    },
    hitBlock: function(reactionTime){
      this.isPlaying = false;
      this.showResult = true;
      this.resultMsg = "Congratulations!";
      this.resultScore = reactionTime;
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
  color: white;
  margin-top: 60px;
}
.welcome{
  border: 10px solid  rgb(17, 155, 63);
  border-radius: 20px;
  padding: 15px 0;
  width: 400px;
  text-align: center;
  color: rgb(17, 155, 63);
  margin: auto;
}
.start{
  border-radius: 20px;
  padding: 15px 0;
  width: 200px;
  background:  rgb(17, 155, 63);
  color: white;
  text-align: center;
  margin: auto;
  cursor: pointer;
}
</style>
